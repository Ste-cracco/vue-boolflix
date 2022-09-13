<template>
    <main>
        <MainHeader @onResponse="setMovies"/> <!-- Invoco l'evento custom e gli passo il metodo -->
        <CreazioneCard :infoFilms="movies" />
    </main>
</template>
  
<script>

import CreazioneCard from "./CreazioneCard.vue"
import MainHeader from "./MainHeader.vue" 
  
export default {
  
    name: 'MainContent',
    components: {
    CreazioneCard,
    MainHeader
}, 

    data() {
        return {
            films: [],
            serieTv: [],
            arrayBandiere: ['en', 'de'],
            posterFilm: [],
            posterSerieTv: []            
        }
    },

    methods: {
        setMovies(movie) { // movie corrisponde a res.data.result (il parametro passato all'evento custom)
            this.films = movie
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

        // series() {
        //     return this.serieTv.map((el) => {
        //         const newSerieTv = {
        //             id: el.id,
        //             titolo: el.name,
        //             titolo_originale: el.original_name,
        //             lingua: el.original_language,
        //             bandiera: '',   
        //             poster: `https://image.tmdb.org/t/p/w342/${el.poster_path}`,
        //             voto: Math.round(el.vote_average / 2)               
        //         }

        //         if(this.arrayBandiere.includes(el.original_language)) {
        //             newSerieTv.bandiera = require(`../assets/${el.original_language}.jpg`)
        //         }

        //     return newSerieTv
        //     })
        // },
    }
}
  
</script>
  
<style lang="scss">
  
</style>
  