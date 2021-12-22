<template>
  <main>
    <ul>
      <li v-for="(film, index) in globalData.films" :key="index">
        <div class="box" v-if="globalData.select == 'movie'">
          <img v-if="film.poster_path != null" :src="'https://image.tmdb.org/t/p/w342' + film.poster_path" :alt="film.title">
          <img v-else :src="'https://image.tmdb.org/t/p/w342' + film.backdrop_path" :alt="film.title">
          <div class="info">
            <h2>{{film.title}}</h2>
            <p>{{film.release_date}}</p>
            <p v-html="'Original language:' + flagIt(film.original_language)"></p>
            <p v-html="'Average vote: ' + starRating(film.vote_average)"></p>
            <p class="overview">Overview: {{film.overview}}</p>
          </div>
        </div>
        <div class="box" v-else>
          <img v-if="film.poster_path != null" :src="'https://image.tmdb.org/t/p/w342' + film.poster_path" :alt="film.name">
          <img v-else :src="'https://image.tmdb.org/t/p/w342' + film.backdrop_path" :alt="film.title">
          <div class="info">
            <h2>{{film.name}}</h2>
            <p>{{film.first_air_date}}</p>
            <p v-html="'Original language: ' + flagIt(film.original_language)"></p>
            <p v-html="'Average vote: ' + starRating(film.vote_average)"></p>
            <p class="overview">Overview: {{film.overview}}</p>
          </div>
        </div>
      </li>
    </ul>
  </main>
</template>

<script>
import globalData from './../assets/globalData';

export default {
  name: 'Main',
  components: {

  },
  data(){
    return {
      globalData,
    }
  },
  methods: {
    flagIt(countryCode) {
      if (countryCode == 'en'){
        countryCode = 'gb';
      } else if ( countryCode == 'ja'){
        countryCode = 'jp';
      }
      return countryCode.toUpperCase().replace(/./g, char => 
          String.fromCodePoint(127397 + char.charCodeAt())
      );
    },
    starRating(rating){
      return '&#11088;'.repeat(Math.floor(rating / 2))
    }
  }
}
</script>

<style lang="scss" scoped>
  main {
    height: 85vh;

    ul {
      height: 100%;
      display: flex;
      align-items: center;
      padding-left: 3rem;
      overflow-x: scroll;

      .box {
        position: relative;
        height: 500px;
        width: 342px;

        img{
          height: 500px;
        }

        img:hover ~ .info {
          display: block;
        }

        .info {
          display: none;
          position: absolute;
          inset: 0;
          user-select: none;
          background-color: rgba($color: #000000, $alpha: 0.4);
          color: white;
          padding: 1rem;

          .overview {
            height: 18.75rem;
            overflow-y: scroll;
            margin-top: .5rem;
          }
        }
      }
    }
  }

</style>