<template>
    <main>
        <SearchBar @onResponseFilm="setFilm" @onResponseSeries="setSerieTv"/> <!-- Invoco l'evento custom e gli passo il metodo -->
        
        <h2>Film:</h2>
        <FilmCard v-for="film in movies" :key="film.id" :film="film"/> <!-- Passo alla props film il valore di 'film' (in movies) -->
        
        <h2>Serie TV:</h2>
        <SerieTvCard v-for="serie in series" :key="serie.id" :serie="serie"/>
    </main>
</template>
  
<script>

import FilmCard from "./FilmCard.vue" 
import SerieTvCard from "./SerieTvCard.vue"
import SearchBar from "./SearchBar.vue"
  
export default {
  
    name: 'MainContent',
    components: {
    FilmCard,
    SerieTvCard,
    SearchBar
}, 

    data() {
        return {
            films: [],
            serieTv: [],
            bandiere: {
                en: require('../assets/en.jpg'),
                de: require('../assets/de.jpg')
            },
            posterSerieTv: []            
        }
    },

    methods: {
        setFilm(movie) { // movie corrisponde a res.data.result (il parametro passato all'evento custom)
            this.films = movie
        },
        setSerieTv(tv) { // tv corrisponde a res.data.result (il parametro passato all'evento custom)
            this.serieTv = tv
        }
    },

    computed: {
        movies() {
            return this.films.map((el) => {
                const newFilms = {
                    id: el.id,
                    titolo: el.title,
                    titolo_originale: el.original_title,
                    lingua: el.original_language,
                    bandiera: this.bandiere[el.original_language], // Accedo in maniera dinamica a una ononima proprotà dell'oggetto bandiere  
                    poster: `https://image.tmdb.org/t/p/w342/${el.poster_path}`,
                    voto: Math.round(el.vote_average / 2)               
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
                    bandiera: this.bandiere[el.original_language], // Accedo in maniera dinamica a una ononima proprotà dell'oggetto bandiere 
                    poster: `https://image.tmdb.org/t/p/w342/${el.poster_path}`,
                    voto: Math.round(el.vote_average / 2)               
                }
            return newSerieTv
            })
        },
    }
}
  
</script>
  
<style lang="scss">
  
</style>
  