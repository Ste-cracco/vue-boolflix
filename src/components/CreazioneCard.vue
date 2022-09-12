<template>
  <div>
    <h3>Film</h3>
    <ul>
      <li v-for="film in infoFilms" :key="film.id">
      {{ film.titolo }} {{ '---' }}
      {{ film.titolo_originale }} {{ '---' }}
      <img :src="stampaBandiere ? film.bandiera : null "> {{ '---' }}
      
      {{ film.voto }}
      </li>
    </ul>

    <h3>Serie TV</h3>
    <ul>
      <li v-for="serie in infoSerieTv" :key="serie.id">
      {{ serie.original_name }} {{ '---' }}
      {{ serie.name }} {{ '---' }}
      {{ serie.original_language }} {{ '---' }}
      {{ serie.vote_average }}
      </li>
    </ul>
  </div>
</template>

<script>



export default {
  name: 'CreazioneCard',
  props: {
    infoFilms: Array,
    infoSerieTv: Array
  },
  data() {
    return {
        arrayBandiere: ['en', 'de', 'it']
    }
  },

  computed: {
      stampaBandiere() {
          this.arrayBandiere.forEach((el) => {
            if(el === 'en' || 'de' || 'it') {
              return true
            }
          })
          return false
      } 
    },
}

</script>

<style lang="scss">

</style>
