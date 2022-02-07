<template>
  <div>
    <nav class="nav-container">
      <div class="logo-container">
        <img src="@/assets/boolflix.png" alt="" /> <span>" tuduuun... "</span>
      </div>
    </nav>
    <div class="video-container">

      <div v-if="show === true" class="search-bar">

        <input
          type="text"
          placeholder="Search Movie"
          v-model="select"
          @keyup.enter="filterMovie(select)"
        />
        <button @click="filterMovie(select)">Search</button>

      </div>

      <img
      v-if="show === false" src="@/assets/boolflix.gif" alt="" />
      
    </div>
  </div>
</template>

<script>
export default {
  name: "App",

  data() {
    return {
      select: "",
    };
  },
  
  props: {
    video: Object,
    show: Boolean,
    popular: Boolean,
  },

  methods: {
    filterMovie(select) {
      this.$emit("movies", select);
      this.$emit("series", select);
      this.select = "";
    },
  },
  
};
</script>

<style lang="scss" scoped>
@import "@/style/header-box.scss";
</style>
