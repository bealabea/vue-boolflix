<template>
    <div v-if="video.flag === true" class="video-container">
    <video autoplay muted id="myVideo">
      <source :src="video.url" type="video/mp4">
    </video>
    </div>
</template>

<script>

export default {
  name: 'App',
  components: {
  },
  data() {
      return {
      
      }
  },
  props: {
      video: Object
  }
}
</script>

<style lang="scss" scoped>
.video-container{
  overflow: hidden;
  video{
        width: 100%;
        position: fixed;
      }
}
</style>