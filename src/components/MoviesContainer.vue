<template>
    <main>
        <h2>MOVIES</h2>
        <div class="container">
            <movie-box v-for="movie in movieList" :key="movie.id" :movie="movie"/>
        </div>
        <h2>SERIES</h2>
        <div class="container">
            <serie-tv-box v-for="serie in seriesList" :key="serie.id" :serie="serie"/>
        </div>
    </main>
</template>

<script>
import MovieBox from './MovieBox.vue'
import SerieTvBox from './SerieTvBox.vue'

export default {
  name: 'App',
  components: {
    MovieBox,
    SerieTvBox
  },
  props: {
      movieList: Array,
      seriesList: Array
  },
}
</script>

<style lang="scss" scoped>
main{
    padding: 100px;
    color: #d4d4d4;
.container {
    display: flex;
    flex-wrap: wrap;
    padding: 20px 0px;
}
}
</style>
