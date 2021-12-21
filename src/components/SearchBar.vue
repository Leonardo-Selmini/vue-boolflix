<template>
  <section>
    <input type="text" placeholder="Inserisci un titolo" v-model="globalData.input">
    <button @click="getFilms">Search</button>
    <select v-model="globalData.select" @change="globalData.films = []">
      <option value="movie" :selected="true">Film</option>
      <option value="tv">Tv Show</option>
    </select>
  </section>
</template>

<script>
import axios from './../../node_modules/axios';
import globalData from './../assets/globalData';

export default {
  name: 'SearchBar',
  data(){
    return {
      globalData,
    }
  },
  methods: {
    getFilms(){
      let url = '';
      if(globalData.select == 'movie'){
        url = 'https://api.themoviedb.org/3/search/movie'
      } else {
        url = 'https://api.themoviedb.org/3/search/tv'
      }
      if(globalData.input != ''){
        axios.get(
          url,{
          params: {
            api_key: 'f3e677cbc259bed9fb123e5be31d467a',
            // language: 'it-IT',
            query: globalData.input
          }
        })
        .then((response)=>{
          // handle success
          console.log(response.data.results);
          console.log(globalData.select);
          globalData.films = response.data.results
        })
        .catch(function (error) {
          // handle error
          console.log(error);
        })
      }
    }
  }
}
</script>

<style lang="scss" scoped>

</style>