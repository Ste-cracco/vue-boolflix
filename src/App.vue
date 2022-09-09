<template>
  <div>
    <input v-model="query" type="text" placeholder="Inserisci nome film">
    <button @click="stampaFilm"> Cerca </button>
    <ul>
      <li v-for="film in films" :key="film.id">
      {{ film.title }}
      </li>
    </ul>

  </div>
</template>

<script>
import axios from "axios"


export default {

  name: 'App',
  components: {

  },

  data() {
    return {
      films: [],
      apiKey: '7ed091e9567506afbcb5cfbea188a586',
      query: 'future'
    }
  },

  // computed:{
  //   stampaFilm() {
  //     return this.recuperaFilm()
  //   }
  // },

  methods: {
    recuperaFilm() {
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=${this.apiKey}&query=${this.query}`)
      .then((res) => {
          this.films = res.data.results
          console.log(this.films)
      })
    },

    stampaFilm() {
      return this.recuperaFilm()
    }
  } 

}

</script>

<style lang="scss">

</style>
