<template>
  <Nav/>
  <Home msg="서진아 힘내!"/>
  <Footer/>
</template>

<script>
import Home from "./components/Home.vue";
import Nav from "./components/layout/Nav.vue";
import Footer from "./components/layout/Footer.vue"
import M from "materialize-css"

export default {
  name: "App",
  components: {
    Home,
    Nav,
    Footer
  },
  mounted: function(){
    M.AutoInit();
  }
};
</script>

<style>

</style>
