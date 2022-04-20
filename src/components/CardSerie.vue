<template>
  <div class="card">
      <p>{{name}}</p>
      <p>{{original_name}}</p>
      <p>{{original_language}}</p>
      <p>{{vote_average}}</p>
  </div>
</template>

<script>
export default {
    name: 'CardSerie',
    props:{
        name: String,
        original_name: String,
        original_language: String,
        vote_average: Number,
        series: Array,
    }
}
</script>

<style lang="scss" scoped>
    
</style>