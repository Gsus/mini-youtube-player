<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <SearchBar @termChange="onTermChange" />
    <main>
      <VideoDetail :clickedVideo="clickedVideo"/>
      <VideoList :videos="videos" @videoClick="onVideoClick"/>
    </main>
  </div>
</template>

<script>
import SearchBar from './components/SearchBar'
import VideoList from './components/VideoList'
import VideoDetail from './components/VideoDetail'
const API_KEY = 'AIzaSyBfCKOOWIE7hGmoRVuLwmDerZOC4T5YXiI';

export default {
  name: 'App',
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },
  data() {
    return {
      videos: null,
      clickedVideo: null
    }
  },
  methods: {
    onTermChange(searchTerm) {
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
    },
    onVideoClick(videoItem) {
      this.clickedVideo = videoItem;
    }
  }
}
</script>

<style lang="scss">
body {
  background-color: #303E50;
  color: #BEBCBC;
  font-family: 'Poppins', sans-serif;
}

#app {
  margin: 0 auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  max-width: 1100px;
  
  & > img {
    width: 100px;
    height: auto;
    position: absolute;
    z-index: -1;
    opacity: 0.6;
  }
}

main {
  margin-top: 2rem;
}

@media (min-width: 769px) {
  main {
    display: flex;
  }
}
</style>
