<template>
  <header>
    <img src="./../assets/netflix-logo.png" alt="">
    <SearchBar/>
  </header>
</template>

<script>
import SearchBar from './SearchBar.vue';

export default {
  name:'Header',
  components: {
    SearchBar,
  }
}
</script>

<style lang="scss" scoped>
  header {
    height: 15vh;
    display: flex;
    align-items: center;
    padding: 0 3rem;

    img {
      height: 90%;
      margin-right: 5rem;
    }
  }

</style>