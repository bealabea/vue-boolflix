<template>
  <div id="app">
    <header-box @movies="movieResearch" @series="seriesResearch" :movieList="movieList" :seriesList="seriesList" :video="video"/>
    <video-bool @movies="movieResearch" @series="seriesResearch" :video="video"/>
    <movies-container :movieList="movieList" :seriesList="seriesList"/>
  </div>
</template>

<script>
  import axios from "axios";
import HeaderBox from './components/HeaderBox.vue';
import MoviesContainer from './components/MoviesContainer.vue';
import VideoBool from './components/VideoBool.vue';

export default {
  name: 'App',
  components: {
    HeaderBox,
    MoviesContainer,
    VideoBool,
  },
  data() {
    return {
    movieList: [],
    seriesList: [],
    video:{url:'/flags/Bool.mp4', flag:true}
    }
  },
  methods: {
    movieResearch(select) {
    axios.get(`https://api.themoviedb.org/3/search/movie/?query=${select}&api_key=5fb1012dc01c82f51045ed3d6d801799`)
    .then((response) => {
      this.movieList = response.data.results;
    });
  },
  seriesResearch(select) {
    axios.get(`https://api.themoviedb.org/3/search/tv/?query=${select}&api_key=5fb1012dc01c82f51045ed3d6d801799`)
    .then((response) => {
      this.seriesList = response.data.results;
    });
  }
}
}
</script>

<style lang="scss">
@import '@/style/main.scss';
</style>
