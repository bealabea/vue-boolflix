<template>
  <main>
    <div v-if="popular === true">
      
      <div class="category-title">
        <h1>Popular Movies</h1>
      </div>
      <div class="container">
        <movie-box
          v-for="movie in movieList"
          :key="movie.id"
          :movie="movie"
          :name="movie.title"
          :originalName="movie.original_title"
          :langList="langList"
        />
      </div>

      <div class="category-title">
        <h1>Popular Series TV</h1>
      </div>
      <div class="container">
        <movie-box
          v-for="movie in seriesList"
          :key="movie.id"
          :movie="movie"
          :name="movie.title"
          :originalName="movie.original_title"
          :langList="langList"
        />
      </div>

    </div>

    <div v-else>

      <div class="category-title">
        <h1>Movies</h1>
      </div>
      <div class="container">
        <movie-box
          v-for="movie in movieList"
          :key="movie.id"
          :movie="movie"
          :name="movie.title"
          :originalName="movie.original_title"
          :langList="langList"
        />
      </div>

      <div class="category-title">
        <h1>Series TV</h1>
      </div>
      <div class="container">
        <movie-box
          v-for="movie in seriesList"
          :key="movie.id"
          :movie="movie"
          :name="movie.name"
          :originalName="movie.original_name"
          :langList="langList"
        />
      </div>

    </div>
  </main>
</template>

<script>
import MovieBox from "./MovieBox.vue";

export default {
  name: "App",

  components: {
    MovieBox,
  },

  props: {
    movieList: Array,
    seriesList: Array,
    langList: Array,
    popular: Boolean,
    show: Boolean,
  },

};
</script>

<style lang="scss" scoped>

main {
  padding: 100px 0;
  color: #bebebe;
  text-align: center;
  .category-title {
    margin: 30px 0;
    padding: 8px 200px;
    text-align: left;
  }
  .container {
    margin: 0 auto;
    display: flex;
    border-radius: 10px;
    background-color: rgba(240, 20, 49, 0.25);
    box-shadow: 0 0 40px 1px rgba(240, 20, 49, 0.52);
    overflow-y: hidden;
    overflow-x: auto;
  }
}
</style>
