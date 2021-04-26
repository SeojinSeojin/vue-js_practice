<template>
  <nav>
    <div class="nav-wrapper">
      <img class="brand-logo center" src="../../assets/logo.png" alt="Vue Logo">
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

export default {
  name: "Nav"
};
</script>

<style scoped>
    img {
        height: 70px;
    }
    nav {
        height:70px;
        background-color: transparent
    }
    .nav-wrapper {
        box-shadow:  0px 10px 50px #989898;
        background-color: #426b5588;
        backdrop-filter: blur(5px);
        position: fixed;
        width: 100%;
        height: 70px;
        z-index: 999;
    }
    .sidenav {
      background-color: rgba(255, 255, 255, 0.6);
      backdrop-filter: blur(5px);
    }
</style>
