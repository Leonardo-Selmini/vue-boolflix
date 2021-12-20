<template>
  <section>
    <input type="text" placeholder="Inserisci un titolo" v-model="input">
    <button @click="getFilms">Search</button>
    <ul>
      <li v-for="(film, index) in films" :key="index">
        <h2>{{film.title}}</h2>
        <p>{{film.release_date}}</p>
        <p>{{film.original_language}}</p>
        <p>{{film.vote_average}}</p>
      </li>
    </ul>
  </section>
</template>

<script>
import axios from './../../node_modules/axios';

export default {
  name: 'SearchBar',
  data(){
    return {
      input: '',
      films: [],
    }
  },
  methods: {
    getFilms(){
      if(this.input != ''){
        axios.get(
          'https://api.themoviedb.org/3/search/movie',{
          params: {
            api_key: 'f3e677cbc259bed9fb123e5be31d467a',
            language: 'it-IT',
            query: this.input
          }
        })
        .then((response)=>{
          // handle success
          this.films = response.data.results
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