<template>
  <div class="header-container">
      <div>BOOLFLIX</div>
      <input type="text" placeholder="Search Movie" v-model="select">
      <button @click="$emit('search', select)">Search</button>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
  
  },
  data(){
      return {
      select: ''
      }
  }
}
</script>

<style lang="scss" scoped>
.header-container {
    background-color: #131313;
    height: 60px;
}
</style>
