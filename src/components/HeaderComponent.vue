<template>
  <header class="container">
      <input type="text" placeholder="Search" v-model="queryStored">
      <button class="btn-danger" @click="search">Search</button>
  </header>
</template>

<script>
export default {
  name: 'HeaderComponent',
  data(){
      return{
         queryStored: '', 
      }
  },
  methods: {
      search(){
        console.log(this.queryStored);
        this.$emit('search', this.queryStored);
      }
  }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">



</style>
