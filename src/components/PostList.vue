<template>
  <div v-if="posts.length>0">
    <h2>Список постов</h2>
    <PostItem
        v-for="post in posts"
        :key="post.id"
        :post="post"
        @remove = "$emit('remove', post)">
    </PostItem>
  </div>
    <h2 v-else style="color: red">Список постов пуст</h2>


</template>

<script>
import PostItem from "@/components/PostItem";
export default {
  name: "PostList",
  components: {PostItem},
  props: {
    posts: {
      type: Array,
      require: true
    },
  }
}
</script>

<style lang="scss" scoped>
   h2 {
        margin: 15px 0;
        color: blue;
      }
</style>