<template>
  <div id="app">
    <SearchBar/>
    <Main/>
  </div>
</template>

<script>
// --import--
import SearchBar from './components/SearchBar.vue';
import Main from './components/Main.vue';

// --export--
export default {
  name: 'App',
  components: {
    SearchBar,
    Main,
  }
}
</script>

<style lang="scss">

</style>
