<template>
  <div class="collection with-header">
    <div href="#!" class="collection-header"><h4>Cheer Up!</h4></div>
  </div>
</template>

<script>
export default {
  name: "ToDoCollection",
  props: {
    msg: String
  },
  data() {
    return{
      todoItems:[]
    }
  },
  created() {
    if(localStorage.length > 0) {
      for(let i=0;i<localStorage.length; i++) {
        this.todoItems.push(localStorage.key(i));
      }
    }
  }
};
</script>

<style scoped>

</style>
