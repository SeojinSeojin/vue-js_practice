<template>
  <div class="home-container">
    <div class="home-sub">
      <h4>{{ msg }}</h4>
      <ToDoInput v-on:saveToDos="saveToDos"/>
      <ToDoCollection v-bind:propsdata="todoItems" />
    </div>
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
  data() {
    return{
      todoItems: []
    }
  },
  created() {
    const todoList = localStorage.getItem("TODOLIST")
    if(todoList !== null) {
      const parsedTodoList = JSON.parse(todoList)
      this.todoItems = parsedTodoList
    }
  },
  components: {
    ToDoCollection,
    ToDoInput
  },
  methods: {
    saveToDos(todo) {
      console.log("home - saveToDos() called")
      const item = todo[0]
      const duedate = todo[1]
      if(localStorage.getItem("TODOLIST") == null) {
          const newTL = [[item, duedate]]
          localStorage.setItem("TODOLIST", JSON.stringify(newTL))
          this.todoItems = newTL
      } else {
          const savedTL = JSON.parse(localStorage.getItem("TODOLIST"))
          console.log(savedTL)
          savedTL.push([item,duedate])
          localStorage.setItem("TODOLIST", JSON.stringify(savedTL))
          this.todoItems = savedTL
      }
    }
  }
};
</script>

<style scoped>
  .home-container {
    display: flex;
    justify-content: center;
  }
  .home-sub {
    height:90vh;
    width: 100%;
    max-width: 650px;
  }
  .collection {
    border-radius: 1rem;
    box-shadow:  0px 20px 50px #989898,
             0px -20px 50px #ffffff;
    transition: .4s;
  }
  .collection:hover {
    box-shadow:  0px 20px 50px #888888,
             0px -20px 50px #f3f3f3;
  }
  h4 {
    text-align: center;
  }
</style>
