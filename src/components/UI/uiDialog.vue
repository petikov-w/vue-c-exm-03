<template>
<!--    <div v-if="show===true" class="dialog" @click="hideDialog"> -->
    <div v-if="show===true" class="dialog" @click="hideDialog">
        <div @click.stop class="dialog__content">
            <slot></slot>
        </div>
    </div>
</template>

<script>
export default {
  name: "ui-dialog",
  props: {
    show: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    hideDialog() {
      this.$emit("update:show", false)
    }
  },
}
</script>

<style lang="scss" scoped>
    .dialog {
      top: 0;
      bottom: 0;
      left: 0;
      right: 0;
      background: rgba(0, 0, 0, 0.5);
      position: fixed;
      display: flex;
    }

    .dialog__content {
      margin: auto;
      background: white;
      border-radius: 12px;
      min-height: 60px;
      min-width: 300px;
      padding: 20px 40px;
    }
</style>