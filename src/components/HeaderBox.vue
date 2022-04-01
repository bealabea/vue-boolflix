<template>
  <div>
    <nav class="nav-container">
      <div class="logo-container">
        <img @click="backToPopular(popular)" src="@/assets/boolflix.png" alt="" /> <span>" tuduuun... "</span>
      </div>
      <ul>
        <li>home</li>
        <li>home</li>
      </ul>
    </nav>
    <div v-if="show" class="search-bar">

        <input
          type="text"
          placeholder="Search Movie"
          v-model="select"
          @keyup.enter="filterMovie(select)"
        />
        <button @click="filterMovie(select)">Search</button> 

    </div>
    
    <transition name="fade">
    <div v-if="!show" class="video-container">

      <img
      src="@/assets/boolflix.gif" alt="" />
      
    </div>
    </transition>

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
