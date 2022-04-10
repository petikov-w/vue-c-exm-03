<template>
  <div>
<!--    <Like></Like>-->
    <Post></Post>
  </div>
</template>

<script>

// import Like from "./components/v-Like"
import Post from "./components/v-Post"
export default {
  name: 'App',
  components: {
    // Like,
    Post
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
