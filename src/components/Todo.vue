<template>
  <div>
    <div class="item-todo">
      <div class="item">
        <input type="checkbox" v-on:change="markCompleted" />
        <p v-bind:class="{'is-complete': todo.completed}">{{todo.title}}</p>
      </div>
      <button class="btn-del" @click="$emit('del-todo', todo.id)">x</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Todo",
  props: ["todo"],
  methods: {
    markCompleted() {
      this.todo.completed = !this.todo.completed;
    }
  }
};
</script>

<style scoped>
.item-todo {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 10px;
  background-color: #eaeaea;
  padding: 10px;
}
.item {
  display: flex;
}

.is-complete {
  text-decoration: line-through;
  font-weight: bold;
}

.btn-del {
  border: none;
  background-color: red;
  color: #fff;
  border-radius: 50%;
  width: 20px;
  height: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}
</style>