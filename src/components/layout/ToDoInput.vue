<template>
    <div class="row">
        <div class="input-field col s4">
          <input id="todo_input" type="text" v-model="newTodoItem">
          <label for="todo_input">Add Your To Dos Here</label>
        </div>
        <div class="input-field col s3">
          <input id="todo_due_date" type="text" class="datepicker">
          <label for="todo_due_date">Due Date</label>
        </div>
        <div class="btn-floating pulse" v-on:click="addToDo"><i class="material-icons">edit</i></div>
    </div>
</template>

<script>

export default {
    name: "ToDoInput",
    data(){
        return {
            newToDoItemDueDate: '',
            newTodoItem: ''
        }
    },
    methods: {
        addToDo() {
            console.log(this.newTodoItem)
            const dueYear = document.querySelector(".year-text").textContent
            const dueDate = document.querySelector(".date-text").textContent
            const dueMonthShort = dueDate.split(" ")[1]
            const monthsShort = ['Jan','Feb','Mar','Apr','May','Jun','Jul','Aug','Sep','Oct','Nov','Dec']
            const dueMonth = monthsShort.indexOf(dueMonthShort) + 1
            const dueDay = dueDate.split(" ")[2]
            this.newToDoItemDueDate = `${dueYear}/${dueMonth}/${dueDay}`
            if(this.newTodoItem == null || this.newToDoItemDueDate == null) {
                //에러처리
            } else {
                localStorage.setItem(this.newTodoItem, this.newToDoItemDueDate)
            }
        },
        clearInputBoxes() {
            this.newToDoItemDueDate = ""
            this.newTodoItem = ""
        }
    }
}
</script>

<style>
.btn-floating {
    background-color: #426b55;
}
</style>
