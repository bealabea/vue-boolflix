<template>
  <div id="app">
    <header-box
      @movies="movieResearch"
      @back="getPopular"
      :movieList="movieList"
      :seriesList="seriesList"
      :popular="popular"
      :show="show"
    />

    <movies-container
      :movieList="movieList"
      :seriesList="seriesList"
      :langList="langList"
      :popular="popular"
      :show="show"
    />
  </div>
</template>

<script>
import axios from "axios";
import HeaderBox from "./components/HeaderBox.vue";
import MoviesContainer from "./components/MoviesContainer.vue";

export default {
  name: "App",

  components: {
    HeaderBox,
    MoviesContainer,
  },

  data() {
    return {
      movieList: [],
      seriesList: [],
      langList: ["en", "it", "ja", "es", "fr", "de"],
      popular: false,
      show: false,
    };
  },

  methods: {
    movieResearch(select) {
      this.popular = false;

      const params = {
        query: select,
        api_key: "5fb1012dc01c82f51045ed3d6d801799",
      };

      axios
        .get(`https://api.themoviedb.org/3/search/movie`, { params })
        .then((response) => {
          this.movieList = response.data.results;
        });
        axios
        .get(`https://api.themoviedb.org/3/search/tv`, { params })
        .then((response) => {
          this.seriesList = response.data.results;
        });
    },

    getPopular() {
      this.movieList = [];
      this.seriesList= [];

      const params = {
        api_key: "5fb1012dc01c82f51045ed3d6d801799",
      };
      this.popular = true;

      axios
        .get(`https://api.themoviedb.org/3/movie/popular`, { params })
        .then((response) => {
          for(let i = 0; i < 10; i++) {
        this.movieList.push(response.data.results[i])
      }
        });
      axios
        .get(`https://api.themoviedb.org/3/tv/popular`, { params })
        .then((response) => {
          for(let i = 0; i < 10; i++) {
        this.seriesList.push(response.data.results[i])
      }
        });
    },
  },

  mounted() {
    setTimeout(() => {
      this.getPopular();
      this.show = true;
    }, 4000);
},
}
</script>

<style lang="scss">
@import url("https://use.fontawesome.com/releases/v5.7.1/css/all.css");
@import "@/style/main.scss";

::-webkit-scrollbar {
  width: 0.5em;
  height: 0.5em;
  margin-right: 10px;
}
::-webkit-scrollbar-thumb {
  min-height: 0.8em;
  min-width: 0.8em;
  background-color: #222;
  border: none;
}
</style>
