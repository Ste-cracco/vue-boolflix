<template>
    <main>
        <input v-model="query" type="text" placeholder="Inserisci nome film">
        <button @click="stampaCard"> Cerca </button>
        <CreazioneCard :infoFilms="movies" :infoSerieTv="series"  />
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
            serieTv: [],
            arrayBandiere: ['en', 'de'],
            posterFilm: [],
            posterSerieTv: [],
            apiKey: '7ed091e9567506afbcb5cfbea188a586',
            query: ''
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
                    bandiera: '',   
                    poster: `https://image.tmdb.org/t/p/w342/${el.poster_path}`,
                    voto: Math.round(el.vote_average / 2)               
                }

                if(this.arrayBandiere.includes(el.original_language)) {
                    newFilms.bandiera = require(`../assets/${el.original_language}.jpg`)
                }

            return newFilms
            })
        },

        series() {
            return this.serieTv.map((el) => {
                const newSerieTv = {
                    id: el.id,
                    titolo: el.name,
                    titolo_originale: el.original_name,
                    lingua: el.original_language,
                    bandiera: '',   
                    poster: `https://image.tmdb.org/t/p/w342/${el.poster_path}`,
                    voto: Math.round(el.vote_average / 2)               
                }

                if(this.arrayBandiere.includes(el.original_language)) {
                    newSerieTv.bandiera = require(`../assets/${el.original_language}.jpg`)
                }

            return newSerieTv
            })
        },
    }
}
  
</script>
  
<style lang="scss">
  
</style>
  