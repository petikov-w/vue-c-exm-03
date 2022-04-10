<template>
  <div>
<!--    <Like></Like>-->
    <PostForm></PostForm>
    <PostList></PostList>
  </div>
</template>

<script>

// import Like from "./components/v-Like"
import PostForm from "./components/PostForm"
import PostList from "./components/PostList"
export default {
  name: 'App',
  components: {
    // Like,
    PostList,
    PostForm
  },
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
    },
  }
}
</script>

<style>
#app {
  padding: 20px;
}
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: sans-serif;
  font-size: 18px;
}

</style>
