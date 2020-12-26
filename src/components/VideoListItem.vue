<template>
  <li>
    <img :src="thumbnailUrl" alt="Video's thumbnail">
    <h1>{{ video.snippet.title }}</h1>
  </li>
</template>

<script>
export default {
  name: 'VideoListItem',
  props: ['video'],
  data() {
    return {
      thumbnailUrl: this.video.snippet.thumbnails.default.url
    }
  }
}
</script>

<style lang="scss" scoped>
li {
  display: flex;
}
</style>