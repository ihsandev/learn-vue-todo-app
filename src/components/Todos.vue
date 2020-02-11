<template>
  <div class="list-todo">
    <div class="item-todo" v-bind:key="todo.id" v-for="todo in todos">
      <Todo v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)" />
    </div>
  </div>
</template>

<script>
import Todo from "./Todo";

export default {
  name: "Todos",
  props: ["todos"],
  components: {
    Todo
  }
};
</script>

<style scoped>
</style>