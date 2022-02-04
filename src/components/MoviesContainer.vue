<template>
  <main>
    <div class="category-title">
      <h1>MOVIES</h1>
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
      <h1>SERIES</h1>
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
  },
};
</script>

<style lang="scss" scoped>
main {
  padding: 100px 0;
  color: #d4d4d4;
  text-align: center;
  .category-title {
    margin: 30px 0;
    background-color: #000;
    padding: 8px;
    width: 100%;
    box-shadow: 0 0 40px 2px #f01330;
  }
  .container {
    max-width: 1800px;
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    padding: 20px 0px;
  }
}
</style>
