<template>
  <section>
    <select v-model="globalData.select" @change="globalData.films = []">
      <option value="movie" :selected="true">Film</option>
      <option value="tv">Tv Show</option>
    </select>
    <input type="text" placeholder="Inserisci un titolo" v-model="globalData.input">
    <button @click="getFilms">Search</button>
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
            language: 'en-EN',
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
  input {
    font-size: 1.2rem;
    background-color: #141414;
    color: white;
    padding: .8rem;
    border: 1px solid #141414;
    outline: none;

    &:focus {
      border: 1px solid white;
    }
  }

  select {
    font-size: 1.2rem;
    background-color: #141414;
    color: white;
    padding: .8rem;
    border: none;
    outline: none;

    &:hover {
      background-color: #222222;
    }
  }

  button {
    font-size: 1.2rem;
    background-color: #141414;
    color: white;
    padding: .8rem;
    border: 1px solid #141414;

    &:hover {
    background-color: #222222;
    }
  }
</style>