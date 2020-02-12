<template>
  <div>
    <form @submit="addTodo" class="input-todo">
      <input v-model="title" type="text" name="title" placeholder="Add Todo .." />
      <input class="btn" type="submit" value="Add" />
    </form>
  </div>
</template>

<script>
// import uuid from "uuid";

export default {
  name: "AddTodo",
  data: function() {
    return {
      title: ""
    };
  },
  methods: {
    addTodo(e) {
      e.preventDefault();
      const newTodo = {
        title: this.title,
        completed: false
      };
      this.$emit("add-todo", newTodo);
    }
  }
};
</script>

<style scoped>
.input-todo {
  display: flex;
  align-items: center;
  margin: 20px 0;
}
.input-todo input[type="text"] {
  width: 100%;
  padding: 10px;
  border: 1px solid black;
}
.btn {
  padding: 10px 20px;
  border: 1px solid black;
  background-color: black;
  color: white;
}
</style>
