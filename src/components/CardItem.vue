<template>
  <div class="card">
      <p>{{item.title || item.name}}</p>
      <p>{{item.original_title || item.original_name}}</p>
      <p>{{item.original_language || item.original_language}}</p>
      <p>{{item.vote_average || item.vote_average}}</p>
  </div>
</template>

<script>
export default {
    name: 'CardItem',
    props: {
        item: Object,
        
    }
}
</script>

<style lang="scss" scoped>

</style>