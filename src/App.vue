<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <div>
      <GetImage btnName="DOG" @getAnimalImage="getImage"/>
      <GetImage btnName="CAT" @getAnimalImage="getImage"/>
    </div>
    <div>
     <img v-bind:src="animalUrl" alt="">
    </div>
  </div>
</template>

<script>
import axios from 'axios'

import GetImage from './components/GetImage.vue'

export default {
  name: 'app',
  components: {
    GetImage
  },
  methods: {
    getImage: function(name) {
      if (name === 'DOG') {
        const DOG_URL = 'https://dog.ceo/api/breeds/image/random'
        axios.get(DOG_URL)
          .then((res) => {
            this.animalUrl = res.data.message
          })
          .catch((err) => {
            console.log(err)
          })
      } else {
        const CAT_URL = 'https://api.thecatapi.com/v1/images/search'
        axios.get(CAT_URL)
          .then((res) => {
            this.animalUrl = res.data[0].url
          })
          .catch((err) => {
            console.log(err)
          })
      }
    }
  },

  data: function() {
    return {
      animalUrl: ''
    }
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
