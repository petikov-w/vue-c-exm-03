<template>
  <div class="post">
    <div>
        <div><strong>Название: </strong>{{ post.title }}</div>
        <div><strong>Описание: </strong>{{ post.body }}</div>
    </div>
    <div class="post__btns">
        <ui-button
            @click = "$emit('remove', post)"
            class="btns">Удалить</ui-button>
    </div>
  </div>
</template>

<script>

export default {
  name: "PostItem",
  props: {
    post: {
      type: Object,
      require: true
    },
  },
}
</script>

<style scoped>
    .post {
      border: 2px solid green;
      padding: 20px;
      margin: 20px 0;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }
    .btns {
      align-self: flex-end;
      color: red;
    }
</style>