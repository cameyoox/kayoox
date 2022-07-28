---
layout: default-es
sitemap: true
---
<script type="text/javascript">var submitted=false;</script>
<iframe name="hidden_iframe" id="hidden_iframe" style="display:none;" onload="if(submitted) {window.location='/es/gracias.html';}"></iframe>
<h1 class="center">Contacto</h1>
<div class="text">
	<form id="form1" class="form" action="https://docs.google.com/forms/u/0/d/e/1FAIpQLSeZ-l47AwUw3ZVsj8c7AJuw5YeJ4SQsM8Mz4kun0Ey0AvaK2g/formResponse" method="post" target="hidden_iframe" onsubmit="submitted=true;">
		<div>
			<label>Asunto</label>
		</div>
		<div>
	    		<input type="text" name="entry.214056702" required title="Este campo es requerido">
	  	</div>
	  	<div>
	    		<label>Mensaje</label>
	  	</div>
		<div>
			<textarea rows="10" name="entry.1681811933" required></textarea>
		</div>
		<div>
			<label class="">Esto es un CAPTCHA. Cuanto son dos por tres?</label>
		</div>
		<div>
	    		<input type="text" name="entry.878377537" required>
	  	</div>
	    <button type="submit">Enviar</button>
	</form>
</div>
<script>
	$('#form1 input[type=text]').on('change invalid', function() {
	    var textfield = $(this).get(0);
	    textfield.setCustomValidity('');
	    
	    if (!textfield.validity.valid) {
	      textfield.setCustomValidity('Este campo es obligatorio');  
	    }
	});

	$('#form1 textarea').on('change invalid', function() {
	    var textfield = $(this).get(0);
	    textfield.setCustomValidity('');
	    
	    if (!textfield.validity.valid) {
	      textfield.setCustomValidity('Este campo es obligatorio');  
	    }
	});
</script>
