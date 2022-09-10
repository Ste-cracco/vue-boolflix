<template>
    <ul>
      <li v-for="film in infoFilms" :key="film.id">
      {{ film.original_title }} {{ '---' }}
      {{ film.title }} {{ '---' }}
      {{ film.original_language }} {{ '---' }} 
      {{ film.vote_average }}
      </li>
    </ul>
</template>
  
<script>
  
  
  
export default {  
  name: 'CreazioneCard',
  props: {
    infoFilms: Array
  },

  components: {

    },  
}
  
</script>
  
<style lang="scss">
  
</style>
  