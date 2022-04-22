<template>
    <section class="container d-flex flex-column mt-5">
        <div class="row">
           <h2 class="mt-5">Movies</h2>
        </div>   
        
        <div class="row d-flex justify-content-between flex-wrap">
           <CardItem class="col-3 gy-3"
            v-for="film in films" :key="film.id"
            :item="film"
           />
        </div>   
        <!-- cycling every film and passing single obj as prop to single generic card -->
        
         
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