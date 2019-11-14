<template>
  <div id="app">

    <img alt="Vue logo" src="./assets/logo.png">

    <GetImage btnName="bark" @getAnimalImage="getImage"/>
    <GetImage btnName="meow" @getAnimalImage="getImage"/>

    <img v-bind:src="animalUrl" alt="">

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
      if (name === 'bark') {
        const DOG_URL = 'https://dog.ceo/api/breeds/image/random'

        axios.get(DOG_URL)
          .then((response) => {
            this.animalUrl = response.data.message
          })
          .catch((error) => {
            console.log(error)
          })
      } else {
        const CAT_URL = 'https://api.thecatapi.com/v1/images/search'

        axios.get(CAT_URL)
          .then((response) => {
            this.animalUrl = response.data[0].url
          })
          .catch((error) => {
            console.log(error)
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