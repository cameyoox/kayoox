---
layout: default-es
---

<div class="row">
  <div class="column">
  	<table>
		<thead>
			<th>
				<div id="image"></div>
			</th>
			<th colspan="2">
				<div id="product"></div>
			</th>
		</thead>
		<thead style="border: 1px solid #696969;">
			<th>Tipo de precio</th>
			<th>Precio</th>
		</thead>
		<tbody>
			<tr>
				<td>Actual</td>
				<td><div id="price"></div></td>
			</tr>
			<tr>
				<td>Máximo</td>
				<td><div id="maxprice"></div></td>
			</tr>
			<tr>
				<td>Mínimo</td>
				<td><div id="minprice"></div></td>	
			</tr>
			<tr>
				<td>Descuento actual</td>
				<td><div class="discount" id="discount"></div></td>	
			</tr>
			<tr>
				<td>Descuento máximo</td>
				<td><div id="maxdiscount"></div></td>	
			</tr>
		</tbody>
	</table>
  </div>
  <div class="column">
  	<div id="diagram"></div>
  </div>
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

		document.getElementById("product").innerHTML = "<a href='https://www.yoox.com/es/" + product + "/item'>" + brand + " - " + category + "</a>";
		document.getElementById("image").innerHTML = "<img src='https://www.yoox.com/images/items/11/" + product + "_14_f.jpg?width=90&amp;height=115&amp;impolicy=crop&amp;gravity=Center' width='90' height='115'/>";
		document.getElementById("diagram").innerHTML = "<img style='border: 1px solid #555; margin: 0;' src='graphs/" + product + ".jpg' width='400'/>"

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
	});
</script>