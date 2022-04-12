<template>
  <div class="App">
<!--    <Like></Like>-->
    <h2>Страница с постами</h2>
    <div class="app__btns">
       <ui-button class="btn-cp" @click="showDialog">Создать пост</ui-button>
       <ui-select></ui-select>
    </div>

    <ui-button class="btn-cp" @click="fetchPosts">Получить посты</ui-button>
    <ui-dialog v-model:show="dialogVisible">
      <PostForm class="dialog" @create="createPostOut"></PostForm>
    </ui-dialog>
    <PostList :posts="posts"
              @remove = "removePost"
              v-if="!isPostLoading">
    </PostList>
    <div class="loading" v-else>Идет загрузка постов...</div>
  </div >
</template>

<script>

// import Like from "./components/v-Like"
import PostForm from "./components/PostForm"
import PostList from "./components/PostList"
import UiDialog from "@/components/UI/uiDialog";
import axios from 'axios'
import UiSelect from "@/components/UI/uiSelect";

export default {
  name: 'App',
  components: {
    UiSelect,
    UiDialog,
    // Like,
    PostList,
    PostForm
  },
  data() {
    return {
      // posts: [
      //   {id: 1, title: 'JavaScript', body: 'Описание поста'},
      //   {id: 2, title: 'JavaScript 1', body: 'Описание поста'},
      //   {id: 3, title: 'JavaScript 2', body: 'Описание поста'},
      // ],
      posts: [],
      dialogVisible: false,
      isPostLoading: false
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
    },
    async fetchPosts() {
      try {
        this.isPostLoading=true;
        // setTimeout(async ()=>{
        //   const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10');
        //   this.posts = response.data;
        //   console.log(response);
        //   this.isPostLoading=false;
        // }, 1000)
          const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10');
          this.posts = response.data;
         // console.log(response);
      } catch (e) {
         alert('Ошибка!')
      } finally {
        this.isPostLoading=false;
      }
    }
  },
  mounted() {
    this.fetchPosts();
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

.loading {
  margin-top: 20px;
  color: cornflowerblue;
}

.app__btns {
  display: flex;
  justify-content: space-between;
}
</style>
