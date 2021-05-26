<template>
  <form class="add-todo__form" id="add-todo-form" @submit.prevent="addTodo">
    <div class="add-todo__form-item flex flex-row">
      <label class="add-todo__form-control_label">
        <input type="checkbox" v-model="licenseAgree" />
        Accept license?
      </label>
      <label class="add-todo__form-control_label">
        <input type="checkbox" v-model="receiveNews" />
        Receive News?
      </label>
    </div>
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
        :disabled="!submitAllowed"
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
      licenseAgree: true,
      receiveNews: true,
    };
  },
  methods: {
    addTodo: function () {
      this.onAddTodo(this.title);
      this.title = "";
    },
  },
  computed: {
    submitAllowed() {
      const { title, licenseAgree, receiveNews } = this;

      return (title.length > 0) & licenseAgree && receiveNews;
    },
  },
};
</script>

<style scoped lang="scss">
.add-todo__form {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
}

.add-todo__form-item {
  &:not(:last-child) {
    margin-bottom: 12px;
  }
}

.add-todo__form-control {
}

.add-todo__form-control_label {
  &:not(:first-child) {
    margin-left: 12px;
  }

  input[type="checkbox"] {
    margin: 0 4px 0 0;
    vertical-align: -1px;
  }
}

.add-todo__form-submit {
}
</style>
