<template>
  <Home msg="Vo Do List" />
  <Footer />
</template>

<script>
import Home from "./components/Home.vue";
import Footer from "./components/layout/Footer.vue";
import M from "materialize-css";

export default {
  name: "App",
  components: {
    Home,
    Footer
  },
  mounted: function() {
    M.AutoInit();
  }
};
</script>

<style>
#app {
  width: 100%;
}
</style>
