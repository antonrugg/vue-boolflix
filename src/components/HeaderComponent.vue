<template>
  <header class="container">
      <input type="text" placeholder="Search" v-model="textToSearch">
      <button class="btn-danger" @click="search">Search</button>
  </header>
</template>

<script>
export default {
  name: 'HeaderComponent',
  data(){
      return{
          textToSearch: ''
      }
  },
  methods: {
      search(){
        console.log(this.textToSearch);
        this.$emit('search', this.textToSearch);
      }
  }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">



</style>
