<template>
    <section class="container d-flex flex-column">
        <div class="row">
           <h2>Movies</h2>
        </div>   
        
        <div class="row">
           <CardItem class="col-3 d-flex flex-wrap"
            v-for="film in films" :key="film.id"
            :item="film"
           />
        </div>   
        
         
    </section>     
</template>

<script>
import CardItem from '@/components/CardItem.vue'

export default {
    name: 'FilmsList',
    components: {
      CardItem,
  },
    props: {
      films: Array,
      
  },
  
}
</script>

<style lang="scss" scoped>

</style>