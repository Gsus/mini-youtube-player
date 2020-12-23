<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <SearchBar @termChange="onTermChange" />
    <!-- VideoDetail -->
    <!-- VideoList -->
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import SearchBar from './components/SearchBar'

export default {
  name: 'App',
  data() {
    return {
      API_KEY: 'AIzaSyBfCKOOWIE7hGmoRVuLwmDerZOC4T5YXiI'
    }
  },
  components: {
    SearchBar
  },
  methods: {
    onTermChange(searchTerm) {
      console.log(searchTerm);
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
