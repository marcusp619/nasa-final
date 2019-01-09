<template>
  <div id="app">
    <Image />
  </div>
</template>

<script>
import Image from './components/Image.vue'

export default {
  name: 'app',
  components: {
    Image
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
