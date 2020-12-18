<template>
<div class="video-result">
  <a :href="linkUrl"><img :src="imageUrl" alt=""></a>
    <VideoResultSection :description="description" :heading="heading"/>
</div>
</template>

<script>
import VideoResultSection from '@/components/VideoResultSection.vue';

export default {
  name: 'VideoResult',
  components: {
    VideoResultSection,
  },
  data() {
    return {
      searchTerm: '',
    };
  },
  props: {
    description: String,
    heading: String,
    imageUrl: String,
    linkUrl: String,
  },
};
</script>
