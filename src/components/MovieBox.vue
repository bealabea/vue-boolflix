<template>
  <div class="movie-box">

    <img
      v-if="movie.poster_path !== null"
      :src="`https://www.themoviedb.org/t/p/original${movie.poster_path}`" alt=""
    />

    <img v-else src="@/assets/not-found.jpg" alt="" />

    <div class="movie-info">
      
      <div class="info-box">
      
        <div class="text-info">
          <strong>Titolo: </strong>
          {{ name }}
        </div>

        <div class="text-info">
          <strong>Titolo originale: </strong>
          {{ originalName }}
        </div>

        <div class="text-info">
          <strong>Voto: </strong>

          <span v-if="movie.vote_average <= 0">0</span>

          <span v-else>
            <i
              v-for="index in getStars(movie.vote_average)"
              :key="index"
              class="icon-color fas fa-star">
            </i>
          </span>
        </div>

        <div class="text-info">
          <strong>Lingua: </strong>
          <span
            v-if="!langList.includes(movie.original_language)">
            {{ movie.original_language }}
          </span>

          <img v-else :src="`/flags/${movie.original_language}.png`" alt=""/>
        </div>

      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",

  props: {
    movie: Object,
    langList: Array,
    name: String,
    originalName: String,
  },

  methods: {
    getStars(vote) {
      return Math.round(vote / 2);
    },
  },
  
};
</script>

<style lang="scss" scoped>
@import "@/style/movie-box.scss";
</style>
