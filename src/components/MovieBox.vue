<template>
  <div class="movie-box" v-if="movie.poster_path !== null">
    <img
      :src="`https://www.themoviedb.org/t/p/original${movie.poster_path}`"
      alt=""/>
    <div class="movie-info">
      <div class="info-box">
        <div class="text-info"><strong>Titolo:</strong> {{ name }}</div>
        <div class="text-info"><strong>Titolo originale:</strong> {{ originalName }}</div>
        <div class="text-info"><strong>Voto:</strong> <i  v-for="index in Math.round(movie.vote_average / 2)" :key="index" class="icon-color fas fa-star"></i></div>
        <div class="text-info"><strong>Overview:</strong> {{ movie.overview }}</div>
        <div class="text-info">
            <strong>Lingua: </strong> <span v-if="!langList.includes(movie.original_language)">{{movie.original_language}}</span>
            <img v-else :src="`/flags/${movie.original_language}.png`" alt=""></div>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  name: "App",
  components: {},
  props: {
    movie: Object,
    langList: Array,
    name: String,
    originalName: String
  },
}
</script>

<style lang="scss" scoped>
@import '@/style/movie-box.scss'
</style>
