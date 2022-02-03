<template>
  <div class="movie-box" v-if="serie.poster_path !== null">
    <img
      :src="`https://www.themoviedb.org/t/p/w300_and_h450_bestv2${serie.poster_path}`"
      alt=""/>
    <div class="movie-info">
      <div class="info-box">
        <div class="text-info"><strong>Titolo:</strong> {{ serie.name }}</div>
        <div class="text-info"><strong>Titolo originale:</strong> {{ serie.original_name }}</div>
        <div class="text-info"><strong>Voto:</strong> {{ serie.vote_average }}</div>
        <div class="text-info"><strong>Overview:</strong> {{ serie.overview }}</div>
        <div class="text-info">
            <strong>Lingua: </strong> <span>{{serie.original_language}} </span>
            <img :src="`/flags/${serie.original_language}.png`" alt=""></div>
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
  },
};
</script>

<style lang="scss" scoped>
@import '@/style/movie-box.scss'
</style>
