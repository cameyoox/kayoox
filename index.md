---
layout: default-en
---

<p>Welcome to Cameyoox! Select a site:</p>

<div class="tiles">
<ul>
	<li>🇪🇸 <a class="" href="#" id="es">España</a></li>
	<li>🇬🇧 <a href="#" id="uk">United Kingdom</a></li>
</ul>
</div>

<script>
	$('#es').on( "click", function() {
		$.cookie('country', 'es');
		window.location.href = "es/index.html";
	});

	$('#uk').on( "click", function() {
		$.cookie('country', 'uk');
		window.location.href = "uk/index.html";
	});

	$(document).ready(function() {
		var country = $.cookie("country");
		if(country != null) {
			window.location = country + '/index.html'
		}
	});
</script>	