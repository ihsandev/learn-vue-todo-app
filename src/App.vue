<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:del-todo="delTodo" />
  </div>
</template>

<script>
import Todos from "./components/Todos";
import Header from "./components/Header";
import AddTodo from "./components/AddTodo";
import axios from "axios";

export default {
  name: "App",
  components: {
    Todos,
    Header,
    AddTodo
  },
  data: function() {
    return {
      todos: []
    };
  },
  methods: {
    delTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(newTodo) {
      axios
        .post("https://jsonplaceholder.typicode.com/todos", newTodo)
        .then(res => (this.todos = [...this.todos, res.data]))
        .catch(err => console.log(err));
    }
  },
  created() {
    axios
      .get(`https://jsonplaceholder.typicode.com/todos?_limit=6`)
      .then(res => (this.todos = res.data))
      .catch(err => console.log(err));
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #2c3e50;
}

#app p {
  margin: 0;
}
</style>
