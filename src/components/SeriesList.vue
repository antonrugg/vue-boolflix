<template>
    <section class="container d-flex flex-column">
      <div class="row">
        <h2>TV Series</h2>
      </div>      
  
      <div class="row d-flex justify-content-between flex-wrap">        
          <CardItem class="col-3 gy-3" 
            v-for="serie in series" :key="serie.id"
           :item="serie"
          />
      </div>  
    </section>    
</template>

<script>

import CardItem from '@/components/CardItem.vue'

export default {
    name: 'SeriesList',
    components: {
      CardItem,
  },
    props:{
        series: Array,
    }
}
</script>

<style lang="scss" scoped>

</style>