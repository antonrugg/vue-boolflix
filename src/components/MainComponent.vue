<template>
  <main>

      <FilmsList :films="films"/>
      <SeriesList :series="series"/>
      
       
  </main>
</template>

<script>

import FilmsList from '@/components/FilmsList.vue'
import SeriesList from '@/components/SeriesList.vue'

export default {
    name: 'MainComponent',
    components: {
    FilmsList,
    SeriesList,
  },
  props: {
      films: Array,
      series: Array,
  }
  
}
</script>

<style lang="scss" scoped>

  main{
    background-color: gray;
  }

</style>