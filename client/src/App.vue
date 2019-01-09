<template>
  <div id="app">
    <ImagesView />
  </div>
</template>

<script>
import ImagesView from './components/ImagesView.vue'

export default {
  name: 'app',
  components: {
    ImagesView
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
