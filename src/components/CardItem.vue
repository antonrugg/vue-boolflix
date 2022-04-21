<template>
  <div class="card ar-card" @mouseover="isHover = true" @mouseleave="isHover = false">

      <img v-show="!isHover" :src="`https://image.tmdb.org/t/p/w342${item.poster_path}`" :alt="item.title || item.name">

      <div class="text-info-container pt-5" v-show="isHover">
        <p><span>Titolo: </span>{{item.title || item.name}}</p>
        <p><span>Titolo Originale: </span>{{item.original_title || item.original_name}}</p>
        <p><span>Linguaggio: </span>{{item.original_language || item.original_language}}</p>
        <p><span>Voto: </span>{{item.vote_average || item.vote_average}}</p>
      </div>
      
  </div>
</template>

<script>
export default {
    name: 'CardItem',
    props: {
        item: Object,
        
    },
    data(){
        return{
            isHover: false
        }
    }
}
</script>

<style lang="scss" scoped>



    .ar-card{
        background-color: black;
        min-height: 200px;
            &:hover{
              transform: transition; 
              transition: 0.3s;
              transition-timing-function: linear;
                }

        .text-info-container{
            height: 100%;
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
            }
        }

    }
</style>