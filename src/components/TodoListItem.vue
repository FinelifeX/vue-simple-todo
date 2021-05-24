<template>
  <li class="todo-list__item" :class="{ 'todo-list__item--done': done }">
    <div class="todo-list__item_content">
      <input
        class="todo-list__item__check"
        :id="`todo-item-check-${item.id}`"
        type="checkbox"
        @click="onChange(item.id)"
      />
      <label class="todo-list__item__title" :for="`todo-item-check-${item.id}`">
        {{ item.title }}
      </label>
    </div>
    <div class="todo-list__item_actions">
      <Button class="todo-list__item_actions__delete" @click="onDelete(item.id)"
        >X</Button
      >
    </div>
  </li>
</template>

<script>
import Button from "./Button";

export default {
  name: "TodoListItem",
  components: { Button },
  props: {
    item: Object,
    onChange: Function,
    onDelete: Function,
  },
  computed: {
    done: function () {
      return this.item.done;
    },
  },
};
</script>

<style scoped lang="scss">
@import "../assets/scss/colors";
@import "../assets/scss/vars";

.todo-list__item {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: stretch;

  &:not(:last-child) {
    margin-bottom: 16px;
  }

  &--done {
    .todo-list__item__title {
      text-decoration: line-through;
    }
  }
}

.todo-list__item_content {
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: flex-start;
  padding: $container-padding-sm;
  border: 1px solid $grey-main;
  border-radius: $border-radius-square;
}

.todo-list__item__check {
  margin: 0;
  vertical-align: -2px;
}

.todo-list__item__title {
  margin-left: 8px;
  text-align: left;
  white-space: normal;
  word-break: break-all;
}

.todo-list__item_actions {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}

.todo-list__item_actions__delete {
}
</style>
