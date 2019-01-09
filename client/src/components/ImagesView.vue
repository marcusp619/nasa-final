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
    name: 'Images',
    data () {
      return {
        query: '',
        images: [],
        POTD: '',
        displayedPic: ''
      }
    },
    methods: {
      getPhotoOfTheDay() {
        const result = this.images.find(image => image.date === 'Wednesday, 1/9/19')
        this.POTD = result;
        this.displayedPic = '';
      },
      prevPhoto() {
        this.POTD = '';
        this.date > 0 ? this.date-- : this.date = 0;
        this.displayedPic = this.images[this.date];
      },
      nextPhoto() {
        this.POTD = '';
        this.date < this.images.length - 1 ? this.date++ : this.date = 30;
        this.displayedPic = this.images[this.date];
      },
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
