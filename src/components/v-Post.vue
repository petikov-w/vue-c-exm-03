<template>
  <div>
    <form @submit.prevent>
      <h2>Создание поста</h2>
      <input :value="title" @input="title=$event.target.value" type="text" placeholder="Название">
      <input :value="body" @input="body=$event.target.value" type="text" placeholder="Описание">
      <button class="btn" @click="createPost">Создать</button>
    </form>
    <div class="post" v-for="post in posts" :key="post.id">
      <div><strong>Название: </strong>{{ post.title }}</div>
      <div><strong>Описание: </strong>{{ post.body }}</div>
    </div>
  </div>

</template>

<script>
export default {
  name: "v-Post",
  data() {
    return {
      posts: [
        {id: 1, title: 'JavaScript', body: 'Описание поста'},
        {id: 2, title: 'JavaScript 1', body: 'Описание поста'},
        {id: 3, title: 'JavaScript 2', body: 'Описание поста'},
      ]
    }
  },
  methods: {
    createPost() {
        const newPost = {
          id: Date.now(),
          title: this.title,
          body: this.body
        }
        this.posts.push(newPost);
        this.title = "";
        this.body = "";
    }
  },
}
</script>

<style lang="scss" scoped>
    .post {
      border: 2px solid green;
      padding: 20px;
      margin: 20px 0;
    }
    form {
      display: flex;
      flex-direction: column;
      h2 {
        margin: 15px 0;
        color: blue;
      }
      input {
        border: 2px solid green;
        margin-bottom: 20px;
        padding: 10px;
      }
    }
    .btn {
      margin-bottom: 20px;
      padding: 10px 15px;
      align-self: flex-end;
      background-color: #d0cccc;
      border: 0;
      &:hover {
        background-color: grey;
        color: white;
      }
     }


</style>