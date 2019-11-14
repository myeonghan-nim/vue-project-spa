<template>
  <div>

    <button v-on:click="getCatImage()">meow!</button>
    
    <img v-bind:src="catImage">

  </div>
</template>

<script>
import axios from 'axios'

export default {
  data: function() {
    return {
      catImage: ''
    }
  },

  methods: {
    getCatImage: function() {
      const CAT_URL = 'https://api.thecatapi.com/v1/images/search'

      axios.get(CAT_URL)
        .then((response) => {
          this.catImage = response.data[0].url
        })
        .catch((error) => {
          console.log(error)
        })
    }
  }
}
</script>

<style>

</style>