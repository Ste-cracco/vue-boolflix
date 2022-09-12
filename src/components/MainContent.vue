<template>
    <main>
        <input v-model="query" type="text" placeholder="Inserisci nome film">
        <button @click="stampaCard"> Cerca </button>
        <CreazioneCard :infoFilms="movies" :infoSerieTv="serieTv" />
    </main>
</template>
  
<script>
import axios from "axios"
import CreazioneCard from "./CreazioneCard.vue" 
  
export default {
  
    name: 'MainContent',
    components: {
    CreazioneCard
    }, 

    data() {
        return {
            films: [],
            newFilms: [],
            serieTv: [],
            apiKey: '7ed091e9567506afbcb5cfbea188a586',
            query: ''
        }
    },

    methods: {
        recuperaInfo() {
            if(this.query.trim() === '') {
                return
            }
            axios.get(`https://api.themoviedb.org/3/search/movie?api_key=${this.apiKey}&query=${this.query}`)
                .then((res) => {
                    this.films = res.data.results
                    console.log('Films:',this.films)
                })
            axios.get(`https://api.themoviedb.org/3/search/tv?api_key=${this.apiKey}&query=${this.query}`)
            .then((res) => {
                    this.serieTv = res.data.results
                    console.log('Serie TV:',this.serieTv)
                })
        },

        stampaCard() {
        return this.recuperaInfo() 
        },

    } ,

    computed: {
        movies() {
            return this.films.map((el) => {
                const newFilms = {
                    id: el.id,
                    titolo: el.title,
                    titolo_originale: el.original_title,
                    lingua: el.original_language,
                    bandiera: require(`../assets/${el.original_language}.jpg`),   
                    voto: Math.round(el.vote_average / 2)               
                }
            return newFilms
            })
        }
    }
}
  
</script>
  
<style lang="scss">
  
</style>
  