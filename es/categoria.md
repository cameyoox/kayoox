---
layout: default-es
datatable: true
sitemap: false
---

<div id="loader" class="full-screen">
    <img class="center-image" src="/assets/images/loading.gif"/>
    <div class="load-text center">Cargando...</div>
</div>

<div class="navbar" onload="alignTop()">
  <a href="/es/categorias/salones.html">SALONES</a>
  <div class="dropdown">
      <button id="boots-menu-btn" class="dropbtn" onclick="showMenu('boots-menu')">BOTAS ▼
      </button>
      <div class="dropdown-content" id="boots-menu">
        <a href="/es/categorias/botas.html">BOTAS</a>
        <a href="/es/categorias/botines.html">BOTINES</a>
        <a href="/es/categorias/botines-biker.html">BOTAS MOTERAS</a>
        <a href="/es/categorias/botines-tejanos.html">BOTAS TEJANAS</a>
        <a href="/es/categorias/botas-altas.html">BOTAS ALTAS</a>
      </div>
  </div> 
  <a href="/es/categorias/bailarinas.html">BAILARINAS</a>
  <a href="/es/categorias/sandalias.html">SANDALIAS</a>
  <a href="/es/categorias/deportivas.html">DEPORTIVAS</a>
  <a href="/es/categorias/espadrillas.html">ESPADRILLAS</a>
  <a href="/es/categorias/zapatos-cordones.html">ZAPATOS DE CORDONES</a>  
  <a href="/es/categorias/mocasines.html">MOCASINES</a>
  <div class="dropdown">
      <button id="other-menu-btn" class="dropbtn" onclick="showMenu('other-menu')">OTROS ZAPATOS ▼
      </button>
      <div class="dropdown-content" id="other-menu">
        <a href="/es/categorias/botas-ski.html">BOTAS DE SKI</a>
        <a href="/es/categorias/playa.html">ZAPATOS DE PLAYA</a>
        <a href="/es/categorias/sandalias-dedo.html">SANDALIAS DE DEDO</a>
        <a href="/es/categorias/zapatos-trekking.html">ZAPATOS DE TREKKING</a>
        <a href="/es/categorias/mules-zuecos.html">MULES Y ZUECOS</a>
      </div>
  </div> 
  <a href="/es/categorias/zapatos.html">VER TODO</a>
</div>

<div class="datatable-begin">
    <table id="example" class="display" style="width:100%">
        <thead>
            <tr>
                <th scope="col">Id</th>
                <th scope="col"></th>
                <th scope="col">Marca<br><input type="search" id="column2" size="15"/></th>
                <th scope="col">Categoría<br><input type="search" id="column3" size="15"/></th>
                <th scope="col">Talla<br><input type="search" id="column4" size="10"/></th>
                <th scope="col">Colores</th>
                <th scope="col">Precio actual</th>
                <th scope="col">Precio máx.</th>
                <th scope="col">Precio min.</th>
                <th scope="col">Descuento actual</th>
            </tr>
        </thead>
    </table>
</div>

<script type="text/javascript">

    function showMenu(menuId) {
        document.getElementById(menuId).classList.toggle("show");
    }

    function hideMenu(menuId) {
        var myDropdown = document.getElementById(menuId);
        if (myDropdown.classList.contains('show')) {
          myDropdown.classList.remove('show');
        }
    }

    window.onclick = function(e) {  
        if(e.target.id =='boots-menu-btn')  {
            hideMenu("other-menu");
        } else if(e.target.id =='other-menu-btn')  {
            hideMenu("boots-menu");
        } else {
            hideMenu("other-menu");
            hideMenu("boots-menu");
        }
    }

    window.onload = function() {
        document.getElementById("content-container").classList.add("content-list-page");
    }
</script>