<template>
  <div class="home">
    <h4>{{ msg }}</h4>
    <ToDoInput/>
    <ToDoCollection/>
  </div>
</template>

<script>
import ToDoCollection from "./layout/ToDoList.vue"
import ToDoInput from "./layout/ToDoInput.vue"

export default {
  name: "Home",
  props: {
    msg: String
  },
  components: {
    ToDoCollection,
    ToDoInput
  },
};
</script>

<style scoped>
  .home {
    height:90vh;
  }
  h4 {
    text-align: center;
  }
</style>
