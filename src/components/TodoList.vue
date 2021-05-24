<template>
  <div class="todo-list__container" v-if="items.length > 0">
    <ul class="todo-list">
      <TodoListItem
        v-for="item of items"
        :key="item.id"
        :item="item"
        :on-change="onItemChange"
        :on-delete="onItemDelete"
      />
    </ul>
  </div>
  <div class="todo-list__container--empty" v-else>
    <p class="todo-list__empty-text">No items yet</p>
  </div>
</template>

<script>
import TodoListItem from "./TodoListItem";

export default {
  name: "TodoList",
  components: { TodoListItem },
  props: {
    items: Array,
    onItemChange: Function,
    onItemDelete: Function,
  },
};
</script>

<style scoped lang="scss">
.todo-list {
  list-style: none;
  padding-inline-start: 0;
  width: 100%;
  max-width: 400px;
}

.todo-list__container {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  margin-top: 16px;

  &--empty {
  }
}

.todo-list__empty-text {
}
</style>
