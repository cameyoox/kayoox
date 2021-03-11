---
layout: default-en
datatable: true
sitemap: false
---

<div id="loader" class="full-screen">
    <img class="center-image" src="/assets/images/loading.gif"/>
    <div class="load-text center">Loading...</div>
</div>

<div class="navbar" onload="alignTop()">
  <a href="/uk/categories/courts.html">COURTS</a>
  <div class="dropdown">
      <button id="boots-menu-btn" class="dropbtn" onclick="showMenu('boots-menu')">BOOTS ▼
      </button>
      <div class="dropdown-content" id="boots-menu">
        <a href="/uk/categories/boots.html">ALL BOOTS</a>
        <a href="/uk/categories/ankle-boots.html">ANKLE BOOTS</a>
        <a href="/uk/categories/biker-boots.html">BIKER BOOTS</a>
        <a href="/uk/categories/cowboy-boots.html">COWBOY BOOTS</a>
        <a href="/uk/categories/knee-high-boots.html">KNEE-HIGH BOOTS</a>
      </div>
  </div> 
  <a href="/uk/categories/ballet-flats.html">BALLET FLATS</a>
  <a href="/uk/categories/sandals.html">SANDALS</a>
  <a href="/uk/categories/sneakers.html">SNEAKERS</a>
  <a href="/uk/categories/espadrilles.html">ESPADRILLES</a>
  <a href="/uk/categories/laced-shoes.html">LACED SHOES</a>
  <a href="/uk/categories/slides-slippers.html">SLIPPERS</a>
  <div class="dropdown">
      <button id="other-menu-btn" class="dropbtn" onclick="showMenu('other-menu')">OTHER SHOES ▼
      </button>
      <div class="dropdown-content" id="other-menu">
        <a href="/uk/categories/apres-ski.html">APRES-SKI</a>
        <a href="/uk/categories/beach.html">BEACH FOOTWEAR</a>
        <a href="/uk/categories/flip-flops.html">FLIP FLOPS</a>
        <a href="/uk/categories/hiking-shoes.html">HIKING SHOES</a>
        <a href="/uk/categories/mules-clogs.html">MULES AND CLOGS</a>
      </div>
  </div> 
  <a href="/uk/categories/shoes.html">ALL SHOES</a>
</div>

<div class="datatable-begin">
    <table id="example" class="display" style="width:100%">
    	<thead>
            <tr>
                <th scope="col">Id</th>
            	<th scope="col"></th>
                <th scope="col">Brand<br><input type="search" id="column2" size="15"/></th>
                <th scope="col">Category<br><input type="search" id="column3" size="15"/></th>
                <th scope="col">Size<br><input type="search" id="column4" size="10"/></th>
                <th scope="col">Colours</th>
                <th scope="col">Current price</th>
                <th scope="col">Max price</th>
                <th scope="col">Min price</th>
                <th scope="col">Current discount</th>
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