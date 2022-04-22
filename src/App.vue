<template>
  <div id="app">
    <HeaderComponent @search="searching"/>  
    <MainComponent :films="films" :series="series" />
    <!-- catching emit and passing props -->
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
    //function to handle user input and api response (emit, v-model in header component)
    searching(searchedInput){
      this.querySearched = searchedInput;
      //enter only if input value is present(true)
      if(!this.input && this.querySearched.length > 0){
        //response from api for movies
        this.queryApi('movie').then((response)=>{
          console.log(response);
          this.films = response.data.results;
          this.input = false;
        });
        //response from api for tv
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
      //generic function for axios request, passing api required params obj in axios.get
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
