<template>
    <section class="container d-flex flex-column">
      <div class="row">
        <h2>Series</h2>
      </div>
      <div class="row">
        <div class="col-2 d-flex flex-wrap">  
          <CardSerie v-for="serie in series" :key="serie.id"
            :name="serie.name"
            :original_name="serie.original_name"
            :original_language="serie.original_language"
            :vote_average="serie.vote_average"
          />
        </div>
      </div>  
    </section>    
</template>

<script>

import CardSerie from '@/components/CardSerie.vue'

export default {
    name: 'SeriesList',
    components: {
      CardSerie,
  },
    props:{
        series: Array,
    }
}
</script>

<style lang="scss" scoped>

</style>