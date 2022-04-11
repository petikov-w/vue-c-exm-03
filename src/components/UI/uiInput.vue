<template>
  <input
      :value="modelValue"
      @input="updateInput"
      class="input"
      type="text">
</template>

<script>
export default {
  name: "ui-input",
  props: {
    modelValue: [String, Number]
  },
  methods: {
    updateInput(event) {
      this.$emit('update:modelValue', event.target.value)
    }
  },
}
</script>

<style lang="scss" scoped>
    .input {
      border: 2px solid green;
      margin-bottom: 20px;
      padding: 10px;
    }
</style>