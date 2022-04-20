<template>
  <div id="app">
    <HeaderComponent />
    <MainComponent />
  </div>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue'
import MainComponent from './components/MainComponent.vue'
import axios from "axios"

export default {
  name: 'App',
  components: {
    HeaderComponent,
    MainComponent,
  },
  data(){
    return{
      apiUrl: 'https://api.themoviedb.org/3/search/',
      apiKey: 'd83a04b61337a081b6c3c318b16a428d',
    }
  },
  mounted(){

    const query = 'verde'

    const params = {
      query,
      api_key: this.apiKey,
      language: 'it-IT',

    }

    axios.get(this.apiUrl + 'tv', {params}).then((response) =>{
      console.log(response);
    }).catch((error) => {
      console.log(error);
    })
  }
}
</script>

<style lang="scss">
  @import '@/styles/general';

  
</style>
