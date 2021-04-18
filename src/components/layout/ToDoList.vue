<template>
  <div class="collection with-header">
    <div href="#!" class="collection-header"><h4>Cheer Up!</h4></div>
    <div class="collection-item" v-bind:key="todoItem" v-for="todoItem in propsdata">{{todoItem[0]}}<span class="badge">{{todoItem[1]}}</span></div>
  </div>
</template>

<script>
export default {
  name: "ToDoCollection",
  props: ["propsdata"]
};
</script>

<style scoped>
  .collection {
    min-height: 20vh;
    max-height: 60vh;
    overflow-y: auto;
  }
</style>
