---
layout: default-en
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
			<th>Price type</th>
			<th>Price</th>
		</thead>
		<tbody>
			<tr>
				<td>Current</td>
				<td><div id="price"></div></td>
			</tr>
			<tr>
				<td>Max</td>
				<td><div id="maxprice"></div></td>
			</tr>
			<tr>
				<td>Min</td>
				<td><div id="minprice"></div></td>	
			</tr>
			<tr>
				<td>Current discount</td>
				<td><div class="discount" id="discount"></div></td>	
			</tr>
			<tr>
				<td>Max. discount</td>
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

		document.getElementById("product").innerHTML = "<a href='https://www.yoox.com/uk/" + product + "/item'>" + brand + " - " + category + "</a>";
		document.getElementById("image").innerHTML = "<img src='https://www.yoox.com/images/items/11/" + product + "_14_f.jpg?width=90&amp;height=115&amp;impolicy=crop&amp;gravity=Center' width='90' height='115'/>";
		document.getElementById("diagram").innerHTML = "<img style='border: 1px solid #555; margin: 0;' src='graphs/" + product + ".jpg' width='400'/>"

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
			document.getElementById("maxdiscount").classList.remove("discount");
		}		
	});
</script>