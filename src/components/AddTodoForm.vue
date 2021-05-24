<template>
  <form class="add-todo__form" id="add-todo-form" @submit.prevent="addTodo">
    <div class="add-todo__form-item">
      <Input
        class="add-todo__form-control"
        id="title"
        name="title"
        v-model="title"
        placeholder="Enter new to-do's title"
        autocomplete="off"
      />
      <Button
        class="add-todo__form-submit"
        type="submit"
        :disabled="title.length < 1"
        >Add</Button
      >
    </div>
  </form>
</template>

<script>
import Button from "./Button";
import Input from "./Input";

export default {
  name: "AddTodoForm",
  components: { Input, Button },
  props: {
    onAddTodo: Function,
  },
  data: function () {
    return {
      title: "",
    };
  },
  methods: {
    addTodo: function () {
      this.onAddTodo(this.title);
      this.title = "";
    },
  },
};
</script>

<style scoped lang="scss">
.add-todo__form {
}

.add-todo__form-item {
}

.add-todo__form-control {
}

.add-todo__form-submit {
}
</style>
