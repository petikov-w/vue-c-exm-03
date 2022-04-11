<template>
  <form @submit.prevent>
    <h2>Создание поста</h2>
    <ui-input
        v-model="post.title"
        type="text"
        placeholder="Название">
    </ui-input>
    <ui-input
        v-model="post.body"
        type="text"
        placeholder="Описание">
    </ui-input>
    <ui-button
        class="btns"
        @click="createPostIn">Создать</ui-button>
  </form>
</template>

<script>
import UiInput from "@/components/UI/uiInput";
export default {
  name: "PostForm",
  components: {UiInput},
  data() {
    return {
      post: {
        title: '',
        body: ''
      }
    }
  },
  methods: {
    createPostIn() {
      this.post.id = Date.now();
      this.$emit('create', this.post);
      this.post = {
        title: "",
        body: ""
      }
    }
  }
}
</script>

<style lang="scss" scoped>
  form {
    display: flex;
    flex-direction: column;
    h2 {
      margin: 15px 0;
      color: blue;
    }
  }

  .btns {
    align-self: flex-end;
  }
</style>