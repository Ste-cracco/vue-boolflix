<template>
    <div>
        <input v-model="query" type="text" placeholder="Inserisci nome film">
        <button @click="stampaCard"> Cerca </button>
    </div>
</template>
  
<script>
import axios from 'axios' 
  
export default {
    name: 'MainHeader',
    data() {
        return {
            query: '',
            apiKey: '7ed091e9567506afbcb5cfbea188a586',
        }
    },
  
    methods: {
        recuperaInfo() {
            if(this.query.trim() === '') {
                return
            }
            // Info Film 
            axios.get(`https://api.themoviedb.org/3/search/movie?api_key=${this.apiKey}&query=${this.query}`)
                .then((res) => {
                    this.films = res.data.results
                    this.posterFilm = res.data.results
                    console.log('Films:',this.films, 'Poster:',this.poster)
                    // Alla risposta del server emettiamo un evento custom e gli passiamo l'array dei film
                    this.$emit('onResponse', res.data.result)
                })
            // Info Serie TV 
            axios.get(`https://api.themoviedb.org/3/search/tv?api_key=${this.apiKey}&query=${this.query}`)
            .then((res) => {
                    this.serieTv = res.data.results
                    this.posterSerieTv = res.data.results
                    console.log('Serie TV:',this.serieTv)
                })
        },

        stampaCard() {
        return this.recuperaInfo() 
        }
    }
}
  
  </script>
  
  <style lang="scss">
  
  </style>
  