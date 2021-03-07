<template>
  <Nav/>
  <HelloWorld msg="서진아 힘내!" />
  <Footer/>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import Nav from "./components/layout/Nav.vue";
import Footer from "./components/layout/Footer.vue"

export default {
  name: "App",
  components: {
    HelloWorld,
    Nav,
    Footer
  }
};
</script>

<style>

</style>
