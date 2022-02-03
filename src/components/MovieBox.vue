<template>
  <div class="movie-box">
      <img :src="`https://www.themoviedb.org/t/p/w300_and_h450_bestv2${movie.poster_path}`" alt="">
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
  
  },
  props: {
      movie: Object
  }
}
</script>

<style lang="scss" scoped>
.movie-box {
    background-color: #1a1a1a;
    height: 300px;
    width: 250px;
    padding: 20px;
    img {
        width: 100%;
    }
}
</style>
