<template>
  <div id="app">
    <HeaderComponent @search="searching"/>
    <MainComponent :films="films" :series="series" />

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
      querySearched: '',
      input: false,
      films: [],
      series: [],
      
    }
  },

  methods: {

    searching(searchedInput){
      this.querySearched = searchedInput;

      if(!this.input && this.querySearched.length > 0){

        this.queryApi('movie').then((response)=>{
          console.log(response);
          this.films = response.data.results;
          this.input = false;
        });

        this.queryApi('tv').then((response) =>{
          console.log(response);
          this.series = response.data.results;
          this.input = false;
        });
      }

    },

    queryTvApi(){
      this.queryApi('tv');
    },

    queryMovieApi(){
      this.queryApi('movie');
    },

    queryApi(searchType){

      this.input = true;

      const params = {
        query: this.querySearched,
        api_key: this.apiKey,
        language: 'it-IT'
    }
    return axios.get(this.apiUrl + searchType, {params}).catch(error => {
      console.log(error);
      this.input = false;
    })
    }
  }

}
</script>

<style lang="scss">
  @import '@/styles/general';

    body{
      background-color: gray;
      overflow-x: hidden;
    }

  
</style>
