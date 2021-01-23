<template>
  <li @click="onVideoClick">
    <img :src="thumbnailUrl" alt="Video's thumbnail">
    <h2>{{ snippetTitle }}</h2>
  </li>
</template>

<script>
import he from "he";

export default {
  name: 'VideoListItem',
  props: ['video'],
  computed: {
    thumbnailUrl() {
      return this.video.snippet.thumbnails.default.url;
    },
    snippetTitle() {
      return he.decode(this.video.snippet.title);
    }
  },
  methods: {
    onVideoClick() {
      this.$emit('videoClick', this.video);
    }
  }
}
</script>

<style lang="scss" scoped>
li {
  text-align: initial;
  display: flex;
  &:hover {
    transition: background 0.4s;
    background-color:  #0e131a;
    cursor: pointer;
  }
}

h2 {
  font-size: 1rem;
  font-weight: normal;
  margin-left: 1.72rem;
}
</style>