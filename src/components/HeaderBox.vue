<template>
  <div class="header-container">
      <div><img src="@/assets/boolflix.png" alt=""> <span>" tuduuun... "</span> </div>
      <div class="search-bar">
      <input type="text" placeholder="Search Movie" v-model="select" @keyup.enter="filterMovie(select, video)">
      <button @click="filterMovie(select, video)">Search</button>
      </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
  },
  props: {
      video: Object,
  },
  data(){
      return {
      select: '',
      }
  },
  methods: {
      filterMovie(select, video) {
        video.flag=false;
        this.$emit('movies', select);
        this.$emit('series', select);
        this.select = '';
      },
  }
}
</script>

<style lang="scss" scoped>
.header-container {
    background-color: #131313;
    padding: 15px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    position: sticky;
    img{
        width: 150px;
    }
    span {
        color: #8d8d8d;
        margin-left: 10px;
        font-style: italic;
    }
    input {
        padding: 8px;
        width: 250px;
        background-color: #3b3b3b;
        border: none;
        outline: none;
        border-radius: 10px;
        color: #8d8d8d;
    }
    button {
        margin-left: 5px;
        padding: 8px 10px;
        border-radius: 10px;
        border: none;
        cursor: pointer;
        background-color: #8d8d8d;
    }
}
</style>
