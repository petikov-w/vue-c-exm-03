<template>
  <div class="App">
<!--    <Like></Like>-->
    <h2>Страница с постами</h2>
    <ui-button class="btn-cp" @click="showDialog">Создать пост</ui-button>
    <ui-dialog v-model:show="dialogVisible">
      <PostForm class="dialog" @create="createPostOut"></PostForm>
    </ui-dialog>

    <PostList :posts="posts"
              @remove = "removePost"></PostList>
  </div>
</template>

<script>

// import Like from "./components/v-Like"
import PostForm from "./components/PostForm"
import PostList from "./components/PostList"
import UiDialog from "@/components/UI/uiDialog";
export default {
  name: 'App',
  components: {
    UiDialog,
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
      ],
      dialogVisible: false,
    }
  },
  methods: {
    createPostOut(post) {
     this.posts.push(post);
      this.dialogVisible = false;
    },
    removePost(post) {
        this.posts = this.posts.filter( p=> p.id !== post.id)
    },
    showDialog() {
      this.dialogVisible = true;
    }
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

.btn-cp {
  margin-top: 15px;
}

</style>
