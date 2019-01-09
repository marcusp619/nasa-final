<template>
  <div>
    <div>
      <button v-on:click="getPhotoOfTheDay()">Photo of the Day </button>
      <button v-on:click="prevPhoto()">Previous Photo </button>
      <button v-on:click="nextPhoto()">Next Photo </button>
      <div>
        <div v-if="POTD">
          <p>{{POTD.title}}</p>
          <img v-bind:src="POTD.url" />
          <p>{{POTD.date}}</p>
        </div>
        <div v-if="displayedPic">
          <p>{{displayedPic.title}}</p>
          <img v-bind:src="displayedPic.url" />
          <p>{{displayedPic.date}}</p>
      </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
    name: 'Image',
    data () {
      return {
        query: '',
        images: [],
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
