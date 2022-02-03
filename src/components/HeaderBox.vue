<template>
  <div class="header-container">
      <div><h1>BOOLFLIX</h1> <span>" tuduuun... "</span> </div>
      <div class="search-bar">
      <input type="text" placeholder="Search Movie" v-model="select" @keyup.enter="filterMovie(select)">
      <button @click="filterMovie(select)">Search</button>
      </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
  },
  data(){
      return {
      select: '',
      }
  },
  methods: {
      filterMovie(select) {
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
    h1 {
        display: inline-block;
        color: red;
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
