<template>
  <main>
    <ul>
      <li v-for="(film, index) in globalData.films" :key="index">
        <div class="info" v-if="globalData.select == 'movie'">
          <img v-if="film.poster_path != null" :src="'https://image.tmdb.org/t/p/w154' + film.poster_path" :alt="film.title">
          <img v-else :src="'https://image.tmdb.org/t/p/w154' + film.backdrop_path" :alt="film.title">
          <h2>{{film.title}}</h2>
          <p>{{film.release_date}}</p>
          <p v-html="'Lingua originale:' + flagIt(film.original_language)"></p>
          <p v-html="starRating(film.vote_average)"></p>
        </div>
        <div class="info" v-else>
          <img v-if="film.poster_path != null" :src="'https://image.tmdb.org/t/p/w154' + film.poster_path" :alt="film.name">
          <img v-else :src="'https://image.tmdb.org/t/p/w154' + film.backdrop_path" :alt="film.title">
          <h2>{{film.name}}</h2>
          <p>{{film.first_air_date}}</p>
          <p v-html="'Lingua originale:' + flagIt(film.original_language)"></p>
          <p v-html="starRating(film.vote_average)"></p>
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

<style>

</style>