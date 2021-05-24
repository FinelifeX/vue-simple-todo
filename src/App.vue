<template>
  <div id="app">
    <h1 class="app__title">Your To Do List</h1>
    <AddTodoForm :on-add-todo="addTodo" />
    <TodoList
      :items="items"
      :on-item-change="updateTodo"
      :on-item-delete="deleteTodo"
    />
  </div>
</template>

<script>
import TodoList from "./components/TodoList";
import AddTodoForm from "./components/AddTodoForm";

import "./App.scss";

export default {
  name: "App",
  components: {
    AddTodoForm,
    TodoList,
  },
  data: function () {
    return {
      currentId: 0,
      items: [],
    };
  },
  methods: {
    addTodo: function (title) {
      console.log(title);
      this.items.push({
        id: this.currentId,
        title,
        done: false,
      });
      this.currentId += 1;
    },
    deleteTodo: function (id) {
      console.log("deleteTodo()", id);
      this.items = this.items.filter((item) => item.id !== id);
    },
    updateTodo: function (id) {
      const itemIdx = this.items.findIndex((item) => item.id === id);

      if (itemIdx < 0) return;

      this.$set(this.items[itemIdx], "done", !this.items[itemIdx].done);
    },
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.app__title {
}
</style>
