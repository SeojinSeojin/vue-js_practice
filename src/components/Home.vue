<template>
  <div class="background"></div>
  <div class="home-container">
    <div class="home-sub">
      <h4 class="blured">{{ msg }}</h4>
      <ToDoInput v-on:saveToDos="saveToDos"/>
      <ToDoCollection v-bind:propsdata="todoItems" v-on:deleteToDos="deleteToDos" v-on:editToDos="editToDos" />
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
    },
    deleteToDos(todo) {
      const savedTL = JSON.parse(localStorage.getItem("TODOLIST"))
      savedTL.forEach(t => {
        if(t[0]==todo[0] & t[1]==todo[1]){
          savedTL.pop(t)
        }
      })
      console.log(savedTL)
      localStorage.setItem("TODOLIST", JSON.stringify(savedTL))
      this.todoItems = savedTL
    },
    editToDos(todo) {
      console.log(todo)
      this.deleteToDos([todo[0], todo[1]])
      this.saveToDos([todo[2], todo[1]])
    }
  }
};
</script>

<style>
  .blured {
    filter: blur(0.5px);
  }
  .home-container {
    display: flex;
    justify-content: center;
  }
  .background {
    position: fixed;
    top: 0;
    width: 100%;
    height: 100vh;
    background-image: url("../assets/sea-unsplash.jpg");
    filter: blur(50px);
  }
  .home-sub {
    height:90vh;
    width: 100%;
    max-width: 650px;
    z-index: 200;
  }
  .collection {
    border-radius: 1rem!important;
    box-shadow:  0px 20px 50px #989898,
             0px -5px 30px #f3f3f3;
    transition: .4s;
    background-color: rgba(255, 255, 255, 0.5)!important;
    backdrop-filter: blur(5px);
  }
  .collection:hover {
    box-shadow:  0px 20px 50px #888888,
             0px -5px 30px #f3f3f3;
  }
  .collection-header, .collection-item {
    background: transparent;
    background-color: rgba(255, 255, 255, 0)!important;
  }
  h4 {
    text-align: center;
  }
  .swal2-popup {
    background-color: rgba(255, 255, 255, 0.6)!important;
    backdrop-filter: blur(8px);
  }
  .swal2-success-circular-line-right, .swal2-success-circular-line-left, .swal2-success-fix {
    background-color: rgba(255, 255, 255, 0)!important;
  }
  .material-tooltip {
    background-color: rgba(200, 200, 200, 0.3)!important;
    backdrop-filter: blur(10px);
    filter: blur(0.5px);
  }
</style>
