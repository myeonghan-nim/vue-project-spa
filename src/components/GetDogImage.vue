<template>
  <div>
    <button v-on:click="getDogImageUrl()">bark!</button>
    <img v-bind:src="dogImage">
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data: function() {
    return {
      dogImage: ''
    }
  },
  methods: {
    getDogImageUrl: function() {
      const DOG_URL = 'https://dog.ceo/api/breeds/image/random'
      axios.get(DOG_URL)
        .then((res) => {
          this.dogImage = res.data.message
        })
        .catch((err) => {
          console.log(err)
        })
    }
  }
}
</script>

<style>
</style>
