---
layout: default-en
---

Welcome to Cameyoox! Select a site:

<table>
	<tr><td>🇪🇸 <a href="#" id="es">España</a></td></tr>
	<tr><td>🇬🇧 <a href="#" id="uk">United Kingdom</a></td></tr>
</table>

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