<template>
<div class="box">
  <div class="like">Количество лайков: <strong>{{ likes }}</strong></div>
  <div class="like" >Количество дизлайков: <strong>{{ dislikes }}</strong></div>
  <button @click="addLike">Лайк</button>
  <button @click="addDisLike">Дизлайк</button>
</div>
</template>

<script>
export default {
  name: "v-Like",
  data() {
    return {
      likes: 0,
      dislikes: 0
    }
  },
  methods: {
    addLike() {
        this.likes += 1;
    },
    addDisLike() {
        this.dislikes += 1;
    }
  }
}
</script>

<style lang="scss" scoped>
    .box {
      margin-top: 30px;
      margin-left: 50px;
    }

    .like {
      font-size: 20px;
      margin-bottom: 20px;
      strong {
        color: forestgreen;
        margin-left: 15px;
      }
    }

</style>