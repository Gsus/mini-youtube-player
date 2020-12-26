<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <SearchBar @termChange="onTermChange" />
    <VideoList :videos="videos" />
    <!-- VideoDetail -->
  </div>
</template>

<script>
import SearchBar from './components/SearchBar'
import VideoList from './components/VideoList'
const API_KEY = 'AIzaSyBfCKOOWIE7hGmoRVuLwmDerZOC4T5YXiI';

export default {
  name: 'App',
  components: {
    SearchBar,
    VideoList
  },
  data() {
    return {
      videos: null,
    }
  },
  methods: {
    onTermChange(searchTerm) {
      // Direct URL. I'll try to construct it in a nicer way
      // fetch(`https://youtube.googleapis.com/youtube/v3/search?part=snippet&q=${searchTerm}&type=video&key=${API_KEY}`)
      // .then(res => console.log(res, searchTerm));

      let baseUrl= 'https://youtube.googleapis.com/youtube/v3/search?';

      let params = new URLSearchParams({
        part: 'snippet',
        q: searchTerm,
        type: 'video',
        key: API_KEY
      });
      
      let finalUrl = baseUrl + params.toString();

      fetch(finalUrl)
        .then(res => res.json())
        .then(data => this.videos = data.items);
        // Note to self: data.items[i].snippet.description/title
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
