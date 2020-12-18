<template>
  <div id="the-app">
    <h1>Video Search</h1>
    <SearchForm v-model:childSearchTerm="parentSearchTerm"/>
    <ul>
      <li v-for="video in displayedVideos" :key="video.id">
        <VideoResult
            :heading="video.title"
            :description="video.description"
            :image-url="video.imageUrl"
            :link-url="video.linkUrl" />
      </li>
    </ul>
    <p v-if="displayedVideos.length === 0">No videos match search.</p>
  </div>
</template>

<script>
import VideoResult from '@/components/VideoResult.vue';
import SearchForm from '@/components/SearchForm.vue';

export default {
  name: 'App',
  components: {
    VideoResult,
    SearchForm,
  },
  data() {
    return {
      videoData: [],
      error: null,
      parentSearchTerm: '',
    };
  },
  created() {
    fetch('http://localhost:8091/videos')
    .then((response) => response.json())
    .then((response) => {
      this.videoData = response.videos;
    }).catch((error) => {
      this.error = error.message;
    });
  },
  computed: {
    displayedVideos() {
      const descriptions = this.videoData.filter((video) => video.description.toLowerCase().replace(/\s+/g, '')
      .includes(this.parentSearchTerm.toLowerCase()));
      console.log('desc');
      console.log(descriptions);
      const titles = this.videoData.filter((video) => video.title.toLowerCase().replace(/\s+/g, '')
      .includes(this.parentSearchTerm.toLowerCase()));
      console.log('titles');
      console.log(titles);
      return [...new Set([...descriptions, ...titles])];
    },
  },
};
</script>

<style lang="scss">
</style>
