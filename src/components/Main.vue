<template>
  <main>
    <ul>
      <li v-for="(film, index) in globalData.films" :key="index">
        <div class="info" v-if="globalData.select == 'movie'">
          <h2>{{film.title}}</h2>
          <p>{{film.release_date}}</p>
          <p v-html="'Lingua originale:' + flagIt(film.original_language)"></p>
          <p>{{film.vote_average}}</p>
        </div>
        <div class="info" v-else>
          <h2>{{film.name}}</h2>
          <p>{{film.first_air_date}}</p>
          <p v-html="'Lingua originale:' + flagIt(film.original_language)"></p>
          <p>{{film.vote_average}}</p>
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
        countryCode = 'gb'
      } else if ( countryCode == 'ja'){
        countryCode = 'jp'
      }
      return countryCode.toUpperCase().replace(/./g, char => 
          String.fromCodePoint(127397 + char.charCodeAt())
      );
    }
  }
}
</script>

<style>

</style>