<template>
  <div class="card ar-card" @mouseover="isHover = true" @mouseleave="isHover = false">

      <img v-show="!isHover" :src="`https://image.tmdb.org/t/p/w342${item.poster_path}`" :alt="item.title || item.name">
    <!-- text inside card showing on hover -->
      <div class="text-info-container pt-5" v-show="isHover">
        <p><span>Titolo: </span>{{item.title || item.name}}</p>
        <p><span>Titolo Originale: </span>{{item.original_title || item.original_name}}</p>
        <p>
            <span>Linguaggio: </span> 
            <country-flag  
            v-if="item.original_language !== 'en'"
            :country='`${item.original_language}`'
             size='small'/>
             <country-flag v-else country="us" size="small"/>
            <!-- using flag icon library found on github: country flag component  -->
        </p>
        
        
        <p>
          <span>
            Voto:  
                <i v-for="(star, i) in starCount" :key="i" class="fas fa-star"></i>
                <i v-for="(star, i) in (5 - starCount)" :key="'A'+ i" class="fa-regular fa-star"></i>
          </span>
        </p>
        <!-- cycling stars empty and bold -->
       
      </div>

  </div>
</template>

<script>
import CountryFlag from 'vue-country-flag'


export default {
    


    name: 'CardItem',
    props: {
        item: Object,
        
    },
    components: {
        CountryFlag,
    },
    data(){
        return{
            isHover: false,
            starCount: Math.round(this.item.vote_average / 2)
            
        }
    }
}
</script>

<style lang="scss" scoped>
    @import url('~@fortawesome/fontawesome-free/css/all.min.css');



    .ar-card{
        background-color: black;
        min-height: 200px;
        cursor: pointer;
        border: 1px solid white;
           

        .text-info-container{
            height: 100%;
             

            i{
                color: yellow;
            }
        }

        img{
            max-height: 100%;
            width: 100%;
        }

        p{
            color: white;
            font-weight: 500;

            span{
                color: white;
                font-weight: 900;
                padding-bottom: 0.3rem;
                margin-right: 0.3rem;
            }
        }

    }
</style>