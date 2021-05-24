<template>
  <input
    class="input"
    v-bind="$attrs"
    :value="value"
    v-on:input="$emit('input', $event.target.value)"
  />
</template>

<script>
export default {
  name: "Input",
  props: ["value"],
};
</script>

<style scoped lang="scss">
@import "../assets/scss/mixins";

.input {
  @include input-default;
}
</style>
