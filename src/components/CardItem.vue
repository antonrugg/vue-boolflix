<template>
  <div class="card ar-card">
      <img :src="`https://image.tmdb.org/t/p/w342${item.poster_path}`" :alt="item.title || item.name">
      <p><span>Titolo: </span>{{item.title || item.name}}</p>
      <p><span>Titolo Originale: </span>{{item.original_title || item.original_name}}</p>
      <p><span>Linguaggio: </span>{{item.original_language || item.original_language}}</p>
      <p><span>Voto: </span>{{item.vote_average || item.vote_average}}</p>
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



    .ar-card{
        background-color: black;

        img{
            height: 150px;
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