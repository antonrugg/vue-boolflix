<template>
  <header class="container-fluid d-flex justify-content-between fixed-top">
      <h1>boolflix</h1>

      <div>
        <input type="text" placeholder="Search" v-model="queryStored">
        <button class="btn-danger" @click="search">Search</button>
      </div>
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
    header{
      background-color: black;
      width: 100vw;
      padding: 1rem 2rem;
      

      h1{
        text-transform: uppercase;
        font-size: 24px;
        font-weight: 700;
        color: red;
      }
    }


</style>
