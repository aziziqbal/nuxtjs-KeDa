<template>
  <label :for="option">
    <input
      type="radio"
      :value="option"
      :id="option"
      @change="$emit('input', $event.target.value)"
      name="radio-input"
      style="margin-left:20px;"
    />
    <slot name="label"/>
  </label>
</template>

<script>
export default {
  props: {
    option: {
      required: true
    },
  },
};
</script>

<style scoped>
label {
  cursor: pointer;
}
</style>