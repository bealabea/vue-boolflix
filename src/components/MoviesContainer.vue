<template>
  <div class="movies-container">
      <movie-box v-for="movie in movieList" :key="movie.id" :movie="movie"/>
  </div>
</template>

<script>
import MovieBox from './MovieBox.vue'

export default {
  name: 'App',
  components: {
    MovieBox
  },
  props: {
      movieList: Array
  }
}
</script>

<style lang="scss" scoped>
.movies-container {
    display: flex;
    flex-wrap: wrap;
    padding: 100px;
}
</style>
