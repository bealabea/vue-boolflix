<template>
  <div class="movie-box" v-if="serie.poster_path !== null">
    <img
      :src="`https://www.themoviedb.org/t/p/w300_and_h450_bestv2${serie.poster_path}`"
      alt=""/>
    <div class="movie-info">
      <div class="info-box">
        <div class="text-info"><strong>Titolo:</strong> {{ serie.name }}</div>
        <div class="text-info"><strong>Titolo originale:</strong> {{ serie.original_name }}</div>
        <div class="text-info"><strong>Voto:</strong> <i  v-for="index in Math.round(serie.vote_average / 2)" :key="index" class="icon-color fas fa-star"></i></div>
        <div class="text-info"><strong>Overview:</strong> {{ serie.overview }}</div>
        <div class="text-info">
            <strong>Lingua: </strong> <span v-if="!langList.includes(serie.original_language)">{{serie.original_language}}</span>
            <img v-else :src="`/flags/${serie.original_language}.png`" alt=""></div>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  name: "App",
  components: {},
  props: {
    serie: Object,
    langList: Array
  },
};
</script>

<style lang="scss" scoped>
@import '@/style/movie-box.scss'
</style>
