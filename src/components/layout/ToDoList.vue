<template>
  <div class="collection with-header">
    <div href="#!" class="collection-header"><h4>Cheer Up!</h4></div>
    <div class="collection-item" v-bind:key="todoItem" v-for="todoItem in propsdata">
      {{todoItem[0]}}
      <span class="badge">
        <i class="material-icons tooltipped" data-position="left" data-tooltip="Complete" v-on:click="onCompleteTodo(todoItem[0])">check</i>
        <i class="material-icons tooltipped" data-position="top" data-tooltip="Edit" v-on:click="onModifyTodo(todoItem[0])">edit</i>
        <i class="material-icons tooltipped" data-position="right" data-tooltip="Delete" v-on:click="onGiveupTodo(todoItem[0])">delete_forever</i>
        {{todoItem[1]}}
      </span>
    </div>
  </div>
</template>

<script>
export default {
  name: "ToDoCollection",
  props: ["propsdata"],
  methods: {
    onCompleteTodo : function(targetTodo) {
      this.$swal.fire({
        title:`Completed ${targetTodo}?`,
        text:"You won't be able to revert this!",
        showCancelButton: true,
        confirmButtonText: "Yes"
      }).then((result)=>{
        if (result.isConfirmed) {
          this.$emit('deleteToDos', targetTodo)
          this.$swal.fire(
            `Completed ${targetTodo}`, "Great Job", 'success'
          )
        }
      })
    },
    onGiveupTodo : function(targetTodo) {
      this.$swal.fire({
        title:`Give Up ${targetTodo}?`,
        text:"You won't be able to revert this!",
        showCancelButton: true,
        confirmButtonText: "Yes"
      }).then((result)=>{
        if (result.isConfirmed) {
          this.$emit('deleteToDos', targetTodo)
          this.$swal.fire(
            `Deleted ${targetTodo}`, "Cheer Up!", 'error'
          )
        }
      })
    },
    onModifyTodo: function(targetTodo) {
      this.$swal.fire({
        title: `Edit ${targetTodo}`,
        input: "text",
        inputLabel: "Input New TODO Name",
        showCancelButton: true,
        inputValidator: (value) => {
          if (!value) {
            return 'You need to write something!'
          }
        }
      }).then((text)=>{
        const newTodo = text.value
        this.$swal.fire(
          `Edited ${targetTodo} -> ${newTodo}`, `Keep Going on ${newTodo}`, 'success'
        )
      })
    }
  }
};
</script>

<style scoped>
  .collection {
    min-height: 20vh;
    max-height: 60vh;
    overflow-y: auto;
    transition: .3s;
  }
  .material-icons {
    cursor:pointer;
    color: grey;
  }
  .material-icons:hover {
    color: green;
  }
</style>
