<template>
  <div id="app">
    <Header/>
    <Main/>
  </div>
</template>

<script>
// --import--
import Header from './components/Header.vue';
import Main from './components/Main.vue';

// --export--
export default {
  name: 'App',
  components: {
    Header,
    Main,
  }
}
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: Arial, Helvetica, sans-serif;
}

body {
  background-color: #141414;
}
</style>
