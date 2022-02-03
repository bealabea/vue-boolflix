<template>
  <div class="movie-box" v-if="movie.poster_path !== null">
    <img
      :src="`https://www.themoviedb.org/t/p/w300_and_h450_bestv2${movie.poster_path}`"
      alt=""/>
    <div class="movie-info">
      <div class="info-box">
        <div class="text-info"><strong>Titolo:</strong> {{ movie.title }}</div>
        <div class="text-info"><strong>Titolo originale:</strong> {{ movie.original_title }}</div>
        <div class="text-info"><strong>Voto:</strong> {{ movie.vote_average }}</div>
        <div class="text-info"><strong>Overview:</strong> {{ movie.overview }}</div>
        <div class="text-info">
            <span><strong>Lingua: </strong>{{movie.original_language}} </span>
            <img :src="`/flags/${movie.original_language}.png`" alt=""></div>
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
  },
};
</script>

<style lang="scss" scoped>
@import '@/style/movie-box.scss'
</style>
