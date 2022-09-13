<template>     
    <div>
        <img :src="serie.poster" alt="">   
        <p>{{ serie.titolo }}</p> 
        <p>{{ serie.titolo_originale }}</p>    
        <img v-if="serie.bandiera" :src="serie.bandiera" >
        <p v-else> {{ serie.lingua }} </p>   

        <li v-for=" n in serie.voto" :key="n">
          <font-awesome-icon icon="fa-solid fa-star" /> 
        </li>
        <li v-for=" n in ( 5 - serie.voto)" :key="n + serie.voto">
          <font-awesome-icon icon="fa-regular fa-star" />       
        </li>   
        <hr>
    </div>    

</template>

<script>

export default {
    name: 'SerieTvCard',
    props: {
        serie: {
            type: Object
        }
    }
}

</script>

<style lang="scss">

</style>
