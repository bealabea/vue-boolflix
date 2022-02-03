<template>
  <div id="app">
    <header-box @search="movieResearch" :movieList="movieList"/>
    <movies-container :movieList="movieList"/>
  </div>
</template>

<script>
  import axios from "axios";
import HeaderBox from './components/HeaderBox.vue';
import MoviesContainer from './components/MoviesContainer.vue';

export default {
  name: 'App',
  components: {
    HeaderBox,
    MoviesContainer
  },
  data() {
    return {
    movieList: [],
    }
  },
  methods: {
    movieResearch(select) {
    axios.get(`https://api.themoviedb.org/3/search/movie/?query=${select}&api_key=5fb1012dc01c82f51045ed3d6d801799`)
    .then((response) => {
      this.movieList = response.data.results;
    });
  }
}
}
</script>

<style lang="scss">
@import '@/style/main.scss';
</style>
