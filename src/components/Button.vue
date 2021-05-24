<template>
  <button class="button" v-bind="$attrs" @click="$emit('click')">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: "Button",
};
</script>

<style scoped lang="scss">
@import "../assets/scss/_mixins.scss";

.button {
  @include button-default;
}
</style>
