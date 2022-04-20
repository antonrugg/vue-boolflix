<template>
    <section class="container d-flex flex-column">
        <div class="row">
           <h2>Movies</h2>
        </div>   
        <div class="row">
        <div class="col-3 d-flex flex-wrap">
           <CardFilm v-for="film in films" :key="film.id"
            :title="film.title"
            :original_title="film.original_title"
            :original_language="film.original_language"
            :vote_average="film.vote_average"
           />
        </div>   
        
         </div>
    </section>     
</template>

<script>
import CardFilm from '@/components/CardFilm.vue'

export default {
    name: 'FilmsList',
    components: {
      CardFilm,
  },
    props: {
      films: Array,
      
  },
  
}
</script>

<style lang="scss" scoped>

</style>