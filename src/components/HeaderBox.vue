<template>
  <div>
    <nav class="nav-container">
      <div class="logo-container">
        <img @click="backToPopular(popular)" src="@/assets/boolflix.png" alt="" /> <span>" tuduuun... "</span>
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
    show: Boolean,
    popular: Boolean,
  },

  methods: {
    filterMovie(select) {
      this.$emit('movies', select);
      this.select = "";
    },
    backToPopular(popular) {
      this.$emit('back', popular);
    },
  },

};
</script>

<style lang="scss" scoped>
@import "@/style/header-box.scss";
</style>
