<template>
  <h1>Todolist</h1>
  <ul>
    <li v-for="(todo, index) in todos" :key="todo.id">
      <span>{{ index + 1 }}.{{ todo.title }}</span>
      <button class="delete-button" @click="deleteTodo(todo, index)">X</button>
    </li>
  </ul>
  <input
    type="text"
    placeholder="New Task"
    v-model="newTodo"
    v-on:keyup.enter="createTodo"
  />
  <button @click="createTodo()">add</button>
</template>

<style scoped>
h1 {
  background-color: lightblue;
  font-family: "Lucida Console", "Courier New", monospace;
  color: rgb(158, 38, 158);
}
button {
  font-size: 20px;
  background-color: white;
  color: rgb(218, 184, 12);
  border: 2px;
}
li {
  font-size: 20px;
  font-family: "Lucida Console", "Courier New", monospace;
}
input {
  font-family: "Lucida Console", "Courier New", monospace;
  font-size: 15px;
}
</style>

<script>
export default {
  name: "Todolist",
  data() {
    return {
      newTodo: "",
      todos: [
        { id: "todo-1", title: "task1" },
        { id: "todo-2", title: "task2" },
      ],
    };
  },
  methods: {
    deleteTodo(todo, index) {
      console.log("delete todo");
      let result = window.confirm("Do you want to delete this item?");
      if (result) {
        this.todos.splice(index, 1);
      }
    },
    createTodo() {
      if (this.newTodo === "") {
        return alert("Write something up!");
      }
      const todoTitle = this.newTodo;
      const todo = {
        title: todoTitle,
        id: "todo-" + this.todos.length + 1,
      };
      this.todos.push(todo);
      this.newTodo = "";
    },
  },
};
</script>