<template>
    <main>
        <h1>MOVIES</h1>
        <div class="container">
            <movie-box v-for="movie in movieList" :key="movie.id" :movie="movie" :langList="langList"/>
        </div>
        <h1>SERIES</h1>
        <div class="container">
            <serie-tv-box v-for="serie in seriesList" :key="serie.id" :serie="serie" :langList="langList"/>
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
      seriesList: Array,
      langList: Array
  },
}
</script>

<style lang="scss" scoped>
main{
    max-width: 1800px;
    margin: 0 auto;
    padding: 100px;
    color: #d4d4d4;
.container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    padding: 20px 0px;
}
}
</style>
