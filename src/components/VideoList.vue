<template>
  <ul>
    <VideoListItem 
      v-for="video in videos" 
      :key="video.etag" 
      :video="video"
      @videoClick="onVideoClick"
    />
  </ul>
</template>

<script>
import VideoListItem from './VideoListItem'

export default {
  name: 'VideoList',
  components: {
    VideoListItem
  },
  props: {
    videos: Array
  },
  methods: {
    onVideoClick(videoItem) {
      this.$emit('videoClick', videoItem);
    }
  }
}
</script>

<style lang="scss" scoped>
ul {
  background-color: #161C24;
  margin-top: 0;
  border-radius: 0.4rem;
  padding: 1.6rem;
}

li {
  list-style: none;
  margin: 0.5rem;
}
</style>