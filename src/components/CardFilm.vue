<template>
  <div class="card">
      <p>{{title}}</p>
      <p>{{original_title}}</p>
      <p>{{original_language}}</p>
      <p>{{vote_average}}</p>
  </div>
</template>

<script>
export default {
    name: 'CardFilm',
    props:{
        title: String,
        original_title: String,
        original_language: String,
        vote_average: Number,
        films: Array,
    }
}
</script>

<style lang="scss" scoped>
     
</style>