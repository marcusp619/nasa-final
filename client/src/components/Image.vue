<template>
  <div>
  </div>
</template>

<script>
export default {
    name: 'Image',
    data () {
      return {
        query: '',
        images: [...images],
        POTD: '',
        displayedPic: ''
      }
    },
    methods: {
      async fetchPhotos() {
        const response = await axios.get('/api/v1/images');
        this.images = response.data.images
      }
    },

    mounted() {
      this.fetchPhotos()
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
