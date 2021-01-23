<template>
  <div v-if="clickedVideo">
    <!-- Embedded video -->
    <iframe width="560" height="315" :src="embeddedUrl" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

    <!-- Title and description -->
    <div id="video-info">
      <h1>{{ title }}</h1>
      <h2>{{ channel }}</h2>
      <p>{{ description }}</p>
    </div>
  </div>
</template>

<script>
import he from 'he';

export default {
  name: 'VideoDetail',
  props: ['clickedVideo'],
  computed: {
    embeddedUrl() {
      return `https://www.youtube.com/embed/${this.clickedVideo.id.videoId}`
    },
    title() {
      return he.decode(this.clickedVideo.snippet.title);
    },
    channel() {
      return he.decode(this.clickedVideo.snippet.channelTitle);
    },
    description() {
      return he.decode(this.clickedVideo.snippet.description);
    }
  }
}
</script>

<style lang="scss" scoped>
iframe {
  border-radius: 0.4rem;
  width: 100%;
}

h1 {
  font-size: 1.7rem;
  margin-bottom: 0;
}

h2 {
  font-size: 1.2rem;
  font-weight: normal;
  margin-top: 0;
}

#video-info {
  background: #161C24;
  text-align: initial;
  border-radius: 0.4rem;
  margin: 1.7rem 0;
  padding: 0.5rem 1.2rem;

  & h1 {
    font-weight: 500;
    line-height: 1.37;
  }
}

@media (min-width: 769px) {
  iframe {
    display: block;
    width: 90%;
  }

  #video-info {
    max-width: 85%;
  }
}
</style>