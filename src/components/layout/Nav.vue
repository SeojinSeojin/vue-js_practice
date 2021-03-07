<template>
  <nav>
    <div class="nav-wrapper">
      <img src="../../assets/logo.png" alt="Vue Logo">
      <a href="#" data-target="mobile-demo" class="sidenav-trigger"><i class="material-icons">menu</i></a>
      <ul class="right hide-on-med-and-down">
        <li><a href="#">Sass</a></li>
        <li><a href="#">Components</a></li>
        <li><a href="#">Javascript</a></li>
        <li><a href="#">Mobile</a></li>
      </ul>
    </div>
  </nav>

  <ul class="sidenav" id="mobile-demo">
    <li><a href="#">Sass</a></li>
    <li><a href="#">Components</a></li>
    <li><a href="#">Javascript</a></li>
    <li><a href="#">Mobile</a></li>
  </ul>
</template>

<script>
import M from "materialize-css"

export default {
  name: "Nav",
  mounted: function(){
    M.AutoInit();
  }
};
</script>

<style scoped>
    img {
        height: 10vh;
    }
    nav {
        height:10vh;
    }
    .nav-wrapper {
        background-color: #426b55;
    }
</style>
