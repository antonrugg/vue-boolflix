<template>
  <div
    class="card ar-card"
    @mouseover="isHover = true"
    @mouseleave="isHover = false"
  >
    <Transition name="fade">
      <img
        v-if="item.poster_path"
        v-show="!isHover"
        :src="`https://image.tmdb.org/t/p/w342${item.poster_path}`"
        :alt="item.title || item.name"
      />
      <p class="not-found" v-else-if="!isHover && !item.poster_path">
        IMG NOT FOUND
      </p>
    </Transition>
    <!-- text inside card showing on hover -->
    <Transition name="fade" mode="out-in">
      <div class="text-info-container pt-5" v-show="isHover">
        <p><span>Titolo: </span>{{ item.title || item.name }}</p>
        <p>
          <span>Titolo Originale: </span
          >{{ item.original_title || item.original_name }}
        </p>
        <p>
          <span>Linguaggio: </span>
          <country-flag
            v-if="item.original_language !== 'en'"
            :country="`${item.original_language}`"
            size="small"
          />
          <country-flag v-else country="us" size="small" />
          <!-- using flag icon library found on github: country flag component  -->
        </p>

        <!-- <p>{{item.id}}</p>
        <p>{{getCast}}</p> -->

        <p>
          <span>
            Voto:
            <i v-for="(star, i) in starCount" :key="i" class="fas fa-star"></i>
            <i
              v-for="(star, i) in 5 - starCount"
              :key="'A' + i"
              class="fa-regular fa-star"
            ></i>
          </span>
        </p>
        <!-- cycling stars empty and bold -->
        <ul>
          <li v-for="actor in cast" :key="actor">{{ actor.name }}</li>
        </ul>
      </div>
    </Transition>
  </div>
</template>

<script>
import CountryFlag from "vue-country-flag";
// import axios from "axios"
import { apiKey } from "@/apikey";

export default {
  name: "CardItem",
  props: {
    item: Object,
  },
  components: {
    CountryFlag,
  },
  data() {
    return {
      isHover: false,
      starCount: Math.round(this.item.vote_average / 2),
      apiUrl: "https://api.themoviedb.org/3/",
      apiKey: apiKey,
      credits: {},
      cast: [],
    };
  },
  methods: {
    // getCast(){
    //     this.cast = [];
    //     axios.get(`${this.apiUrl}${this.searchType}/${this.item.id}/credits?${apiKey}`)
    //          .then((response) =>{
    //              this.credit = response.data;
    //              console.log('credit', this.credit)
    //              for (let i = 0; i < this.credit.cast.length; i++) {
    //                  if (i < 5) {
    //                         this.cast.push(this.credit.cast[i]);
    //                     }
    //   }
    //          })
    //          return this.cast;
    // }
  },
};
</script>

<style lang="scss" scoped>
@import url("~@fortawesome/fontawesome-free/css/all.min.css");

.ar-card {
  background-color: black;
  min-height: 200px;
  max-height: 400px;
  cursor: pointer;
  border: 1px solid white;

  .text-info-container {
    height: 100%;
    position: absolute;

    i {
      color: yellow;
    }
  }

  img {
    max-height: 100%;
    width: 100%;
  }

  p {
    color: white;
    font-weight: 500;

    span {
      color: white;
      font-weight: 900;
      padding-bottom: 0.3rem;
      margin-right: 0.3rem;
    }
  }

  .not-found {
    position: absolute;
    top: 50%;
    right: 50%;
    transform: translate(50%, -50%);
  }
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.2s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>