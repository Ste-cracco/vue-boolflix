<template>     
      <div>
          <img :src="film.poster" alt="">   
          <p>{{ film.titolo }}</p> 
          <p>{{ film.titolo_originale }}</p>    
          <img v-if="film.bandiera" :src="film.bandiera" >
          <p v-else> {{ film.lingua }} </p>   

          <li v-for=" n in film.voto" :key="n">
            <font-awesome-icon icon="fa-solid fa-star" /> 
          </li>
          <li v-for=" n in ( 5 - film.voto)" :key="n + film.voto">
            <font-awesome-icon icon="fa-regular fa-star" />       
          </li>   
          <hr>
      </div>    

</template>

<script>

export default {
  name: 'FilmCard',
  props: {
    film: {
      type: Object
    }
  }
}

</script>

<style lang="scss">

</style>
