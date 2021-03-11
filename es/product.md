---
layout: default-es
locale: es_ES
title: Consigue las mejores ofertas de Yoox
description: Nos encantan los zapatos y los descuentos
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
		<li><div class="productDetail">Precio actual:</div> <div id="price" class="left-align"></div></li>
		<li><div class="productDetail">Precio máximo:</div> <div id="maxprice" class="left-align"></div></li>
		<li><div class="productDetail">Precio mínimo:</div> <div id="minprice" class="left-align"></div></li>	
		<li><div class="productDetail">Descuento actual:</div> <div class="discount left-align" id="discount"></div></li>
		<li><div class="productDetail">Descuento máximo:</div> <div id="maxdiscount" class="left-align"></div></li>
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

		document.getElementById("product").innerHTML = "<a href='https://www.yoox.com/es/" + product + "/item' class='detail-margin button-text'>COMPRAR " + category.toUpperCase() + " " + brand + "</a>";

		document.getElementById("product2").innerHTML = "<a href='https://www.yoox.com/es/" + product + "/item' class='detail-margin button-text'>COMPRAR " + category.toUpperCase() + " " + brand + "</a>";

		var prefix = product.substring(0,2)
		document.getElementById("image").innerHTML = "<img src='https://www.yoox.com/images/items/" + prefix + "/" + product + "_14_f.jpg?width=350&amp;height=490&amp;impolicy=crop&amp;gravity=Center' width='350' height='490' class='detail-margin'/>";

		document.getElementById("price").innerHTML = parseFloat(price).toLocaleString('es-ES', { style: 'currency', currency: 'EUR' })
		document.getElementById("maxprice").innerHTML = parseFloat(maxprice).toLocaleString('es-ES', { style: 'currency', currency: 'EUR' })
		document.getElementById("minprice").innerHTML = parseFloat(minprice).toLocaleString('es-ES', { style: 'currency', currency: 'EUR' })

		if(parseFloat(price) < parseFloat(maxprice)) {
			document.getElementById("discount").innerHTML = (parseFloat(maxprice) - parseFloat(price)).toLocaleString('es-ES', { style: 'currency', currency: 'EUR' })
		} else {
			document.getElementById("discount").innerHTML = "Sin descuento"
			document.getElementById("discount").classList.remove("discount");
		}

		if(parseFloat(minprice) < parseFloat(maxprice)) {
			document.getElementById("maxdiscount").innerHTML = (parseFloat(maxprice) - parseFloat(minprice)).toLocaleString('es-ES', { style: 'currency', currency: 'EUR' })
		} else {
			document.getElementById("maxdiscount").innerHTML = "Sin descuento"
		}

		$.getJSON('/assets/data/diagram-data-es.txt', function(data) {
		})
		.fail(function(jqXHR, textStatus, errorThrown) {
	        console.log("error " + textStatus);
	        console.log("incoming Text " + jqXHR.responseText);
    	})
    	.done(function(data){
    		var ctx = document.getElementById('myChart').getContext('2d');

			var myChart = new Chart(ctx, {
		        type: 'line',
		        data: {
		            datasets: [{
		                label: 'Precio',
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
		                text: 'Evolución del precio de ' + product
		            },
		            scales: {
		            	xAxes: [{
							type:'time',
							position: 'bottom',
							time: {
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
				                return tooltipItem.yLabel + '€';
		            		}
		        		}
   					}
		        }
			});
		});

		document.title = brand + ' ' + category + ' | Cameyoox'
	});
</script>