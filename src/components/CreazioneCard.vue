<template>
  <div>
    <h3>Film</h3>   
      <div v-for="film in infoFilms" :key="film.id">
        <img :src="film.poster" alt="">   
        <p>{{ film.titolo }}</p> 
        <p>{{ film.titolo_originale }}</p>    
        <img :src="film.bandiera " v-if="film.bandiera">
        <p v-else> {{ film.lingua }} </p>   

        <li v-for=" n in film.voto" :key="n">
          <font-awesome-icon icon="fa-solid fa-star" /> 
        </li>
        <li v-for=" n in ( 5 - film.voto)" :key="n + film.voto">
          <font-awesome-icon icon="fa-regular fa-star" />       
        </li>     

        <hr>
      </div>
    

    <h3>Serie TV</h3>
      <div v-for="serie in infoSerieTv" :key="serie.id">
        <img :src="serie.poster" alt="">  
        <p>{{ serie.titolo }}</p> 
        <p>{{ serie.titolo_originale }}</p>   
        <img :src="serie.bandiera " v-if="serie.bandiera">
        <p v-else> {{ serie.lingua }} </p> 
        <li v-for=" n in serie.voto" :key="n">
          <font-awesome-icon icon="fa-solid fa-star" /> 
        </li>
        <li v-for=" n in ( 5 - serie.voto)" :key="n + serie.voto">
          <font-awesome-icon icon="fa-regular fa-star" />       
        </li>        
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
