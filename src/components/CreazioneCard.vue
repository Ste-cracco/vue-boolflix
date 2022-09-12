<template>
  <div>
    <h3>Film</h3>   
      <div v-for="film in infoFilms" :key="film.id">
        <img :src="film.poster" alt="">   
        <p>{{ film.titolo }}</p> 
        <p>{{ film.titolo_originale }}</p>    
        <img :src="film.bandiera " v-if="film.bandiera">
        <p v-else> {{ film.lingua }} </p> 
        <p> {{ film.voto }}</p>    
        <hr>
      </div>
    

    <h3>Serie TV</h3>
      <div v-for="serie in infoSerieTv" :key="serie.id">
        <img :src="serie.poster" alt="">  
        <p>{{ serie.titolo }}</p> 
        <p>{{ serie.titolo_originale }}</p>   
        <img :src="serie.bandiera " v-if="serie.bandiera">
        <p v-else> {{ serie.lingua }} </p> 
        <p> {{ serie.voto }}</p>    
        <hr>
      </div>
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
        
    }
  },

  computed: {
      
    },
}

</script>

<style lang="scss">

</style>
