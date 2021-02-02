---
layout: default-en
sitemap: false
graph: true
---

<div id="product"></div>
<div id="image"></div>

<ul>
	<li><div class="productDetail">Current price:</div> <div id="price"></div></li>
	<li><div class="productDetail">Max price:</div> <div id="maxprice"></div></li>
	<li><div class="productDetail">Min price:</div> <div id="minprice"></div></li>	
	<li><div class="productDetail">Current discount:</div> <div class="discount" id="discount"></div></li>
	<li><div class="productDetail">Max discount:</div> <div id="maxdiscount"></div></li>
</ul>

<div style="width: 375px; height: 300px;"><canvas id="myChart" className="chartjs"></canvas></div>

<script>
	window.addEventListener("load", function(){
		urlParams = new URLSearchParams(window.location.search);
		
		product = urlParams.get('product')
		brand = urlParams.get('brand')
		category = urlParams.get('category')
		price = urlParams.get('price')
		maxprice = urlParams.get('maxprice')
		minprice = urlParams.get('minprice')

		document.getElementById("product").innerHTML = "<a href='https://www.yoox.com/uk/" + product + "/item'>" + brand + " - " + category + "</a>";
		document.getElementById("image").innerHTML = "<img src='https://www.yoox.com/images/items/11/" + product + "_14_f.jpg?width=90&amp;height=115&amp;impolicy=crop&amp;gravity=Center' width='90' height='115'/>";

		document.getElementById("price").innerHTML = parseFloat(price).toLocaleString('en-GB', { style: 'currency', currency: 'GBP' })
		document.getElementById("maxprice").innerHTML = parseFloat(maxprice).toLocaleString('en-GB', { style: 'currency', currency: 'GBP' })
		document.getElementById("minprice").innerHTML = parseFloat(minprice).toLocaleString('en-GB', { style: 'currency', currency: 'GBP' })
	
		if(parseFloat(price) < parseFloat(maxprice)) {
			document.getElementById("discount").innerHTML = (parseFloat(maxprice) - parseFloat(price)).toLocaleString('en-GB', { style: 'currency', currency: 'GBP' })
		} else {
			document.getElementById("discount").innerHTML = "None"
			document.getElementById("discount").classList.remove("discount");
		}

		if(parseFloat(minprice) < parseFloat(maxprice)) {
			document.getElementById("maxdiscount").innerHTML = (parseFloat(maxprice) - parseFloat(minprice)).toLocaleString('en-GB', { style: 'currency', currency: 'GBP' })
		} else {
			document.getElementById("maxdiscount").innerHTML = "None"
		}	

		$.getJSON('/assets/data/diagram-data-uk.txt', function(data) {
		})
		.fail(function(jqXHR, textStatus, errorThrown) {
	        console.log("error " + textStatus);
	        console.log("incoming Text " + jqXHR.responseText);
    	})
    	.done(function(data){
    		var ctx = document.getElementById('myChart').getContext('2d');
    		console.log('data' + JSON.stringify(data.data[product]))

			var myChart = new Chart(ctx, {
		        type: 'line',
		        data: {
		            datasets: [{
		                label: 'Price',
		                fill: false,
		                data: data.data[product],
		                backgroundColor: 'blue',
		                borderColor: 'blue',
		            }],
		        },
		        options: {
		        	responsive: true,
    				maintainAspectRatio: false,
		            title: {
		                display: true,
		                text: 'Price evolution of ' + product
		            },
		            scales: {
		            	xAxes: [{
							type:'time',
							position: 'bottom',
							time: {
							    tooltipFormat:'DD/MM/YYYY',
			              		parser: 'YYYY-MM-DD',
			              		unit: 'day',
			              		displayFormats: {
			                		'day': 'DD/MM/YYYY'
			              		}
			          		},
							distribution: 'series'
						}]
		            },
		            tooltips: {
		            	custom: function(tooltip) {
					        tooltip.displayColors = false;
				        },
				        callbacks: {
				            label: function(tooltipItem, data) {
				                return '£' + tooltipItem.yLabel;
		            		}
		        		}
   					 }
		        }
			});
    	});
	});
</script>