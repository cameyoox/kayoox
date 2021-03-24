---
layout: default-us
sitemap: false
graph: true
---

<div class="center-all bottom-separation">
	<div id="product"></div>
</div>

<div class="center-detail">
	<div id="image"></div>
	<div class="tiles center-all">
	<ul>
		<li><div class="productDetail">Current price:</div> <div id="price" class="left-align"></div></li>
		<li><div class="productDetail">Max price:</div> <div id="maxprice" class="left-align"></div></li>
		<li><div class="productDetail">Min price:</div> <div id="minprice" class="left-align"></div></li>	
		<li><div class="productDetail">Current discount:</div> <div class="discount left-align" id="discount"></div></li>
		<li><div class="productDetail">Max discount:</div> <div id="maxdiscount" class="left-align"></div></li>
	</ul>
	</div>
	<div class="center-detail diagram"><canvas id="myChart" className="chartjs"></canvas></div>
</div>

<div class="center-all">
	<div id="product2"></div>
</div>

<script>
	window.addEventListener("load", function(){
		urlParams = new URLSearchParams(window.location.search);
		
		product = urlParams.get('product')
		brand = urlParams.get('brand')
		category = urlParams.get('category')
		price = urlParams.get('price')
		maxprice = urlParams.get('maxprice')
		minprice = urlParams.get('minprice')

		document.getElementById("product").innerHTML = "<a href='https://www.yoox.com/us/" + product + "/item' class='detail-margin button-text'>BUY NOW " + category.toUpperCase() + " " + brand + "</a>";

		document.getElementById("product2").innerHTML = "<a href='https://www.yoox.com/us/" + product + "/item' class='detail-margin button-text'>BUY NOW " + category.toUpperCase() + " " + brand + "</a>";

		var prefix = product.substring(0,2)
		document.getElementById("image").innerHTML = "<img src='https://www.yoox.com/images/items/" + prefix + "/" + product + "_14_f.jpg?width=350&amp;height=490&amp;impolicy=crop&amp;gravity=Center' width='350' height='490' class='detail-margin'/>";

		document.getElementById("price").innerHTML = parseFloat(price).toLocaleString('en-US', { style: 'currency', currency: 'USD' })
		document.getElementById("maxprice").innerHTML = parseFloat(maxprice).toLocaleString('en-US', { style: 'currency', currency: 'USD' })
		document.getElementById("minprice").innerHTML = parseFloat(minprice).toLocaleString('en-US', { style: 'currency', currency: 'USD' })
	
		if(parseFloat(price) < parseFloat(maxprice)) {
			document.getElementById("discount").innerHTML = (parseFloat(maxprice) - parseFloat(price)).toLocaleString('en-US', { style: 'currency', currency: 'USD' })
		} else {
			document.getElementById("discount").innerHTML = "None"
			document.getElementById("discount").classList.remove("discount");
		}

		if(parseFloat(minprice) < parseFloat(maxprice)) {
			document.getElementById("maxdiscount").innerHTML = (parseFloat(maxprice) - parseFloat(minprice)).toLocaleString('en-US', { style: 'currency', currency: 'USD' })
		} else {
			document.getElementById("maxdiscount").innerHTML = "None"
		}	

		$.getJSON('/assets/data/diagram-data-us.txt', function(data) {
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
							    tooltipFormat:'MM/DD/YYYY',
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
				                return '$' + tooltipItem.yLabel;
		            		}
		        		}
   					}
		        }
			});
    	});

    	document.title = brand + ' ' + category + ' | Cameyoox'
	});
</script>