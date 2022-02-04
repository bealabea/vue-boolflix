<template>
  <div id="app">
    <header-box @movies="movieResearch" @series="seriesResearch" :movieList="movieList" :seriesList="seriesList" :video="video"/>
    <movies-container :movieList="movieList" :seriesList="seriesList" :langList="langList"/>
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
    MoviesContainer,

  },
  data() {
    return {
    movieList: [],
    seriesList: [],
    video:{url:'@/assets/boolflix.gif', flag:true},
    langList: ['en', 'it', 'ja', 'es', 'fr', 'de']
    }
  },
  methods: {
    movieResearch(select) {
      const params = {
        query: select,
        api_key: '5fb1012dc01c82f51045ed3d6d801799'
      }

    axios.get(`https://api.themoviedb.org/3/search/movie`, {params})
    .then((response) => {
      this.movieList = response.data.results;
    });
  },
  seriesResearch(select) {
    const params = {
        query: select,
        api_key: '5fb1012dc01c82f51045ed3d6d801799'
      }

    axios.get(`https://api.themoviedb.org/3/search/tv`, {params})
    .then((response) => {
      this.seriesList = response.data.results;
    });
  }
}
}
</script>

<style lang="scss">
@import url('https://use.fontawesome.com/releases/v5.7.1/css/all.css');
@import '@/style/main.scss';
</style>
