---
layout: default-us
datatable: true
sitemap: false
---

<div id="loader" class="full-screen">
    <img class="center-image" src="/assets/images/loading.gif"/>
    <div class="load-text center">Loading...</div>
</div>

<div class="navbar" onload="alignTop()">
  <a href="/us/categories/pumps.html">PUMPS</a>
  <div class="dropdown">
      <button id="boots-menu-btn" class="dropbtn" onclick="showMenu('boots-menu')">BOOTS ▼
      </button>
      <div class="dropdown-content" id="boots-menu">
        <a href="/us/categories/boots.html">ALL BOOTS</a>
        <a href="/us/categories/ankle-boots.html">ANKLE BOOTS</a>
        <a href="/us/categories/biker-boots.html">BIKER BOOTS</a>
        <a href="/us/categories/cowboy-boots.html">COWBOY BOOTS</a>
        <a href="/us/categories/knee-high-boots.html">KNEE-HIGH BOOTS</a>
      </div>
  </div> 
  <a href="/us/categories/ballet-flats.html">BALLET FLATS</a>
  <a href="/us/categories/sandals.html">SANDALS</a>
  <a href="/us/categories/sneakers.html">SNEAKERS</a>
  <a href="/us/categories/espadrilles.html">ESPADRILLES</a>
  <a href="/us/categories/laced-shoes.html">LACED SHOES</a>
  <a href="/us/categories/slides-slippers.html">SLIPPERS</a>
  <div class="dropdown">
      <button id="other-menu-btn" class="dropbtn" onclick="showMenu('other-menu')">OTHER SHOES ▼
      </button>
      <div class="dropdown-content" id="other-menu">
        <a href="/us/categories/apres-ski.html">APRES-SKI</a>
        <a href="/us/categories/beach.html">BEACH FOOTWEAR</a>
        <a href="/us/categories/flip-flops.html">FLIP FLOPS</a>
        <a href="/us/categories/hiking-shoes.html">HIKING SHOES</a>
        <a href="/us/categories/mules-clogs.html">MULES AND CLOGS</a>
      </div>
  </div> 
  <a href="/us/categories/shoes.html">ALL SHOES</a>
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