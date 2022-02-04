<template>
  <div>
    <div class="logo-container">
      <img src="@/assets/boolflix.png" alt="" /> <span>" tuduuun... "</span>
    </div>
    <div class="video-container">
        <div v-if="flag === true" class="search-bar">
        <input
          type="text"
          placeholder="Search Movie"
          v-model="select"
          @keyup.enter="filterMovie(select, video)"
        />
        <button @click="filterMovie(select, video)">Search</button>
      </div>
      <img v-if="video.flag === true" src="@/assets/boolflix.gif" alt="" />

      
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
  props: {
    video: Object,
  },
  data() {
    return {
      select: "",
      flag: false
    };
  },
  methods: {
    filterMovie(select, video) {
      video.flag = false;
      this.$emit("movies", select);
      this.$emit("series", select);
      this.select = "";
    },
    },
    mounted() {
        setTimeout(() => {this.flag = true}, 3500);
    }
}
</script>

<style lang="scss" scoped>
@import "@/style/header-box.scss";
</style>
