<template>
  <section  class="video-result-section">
    <h2>{{ heading }}</h2>
    <p>
      {{ description }}
    </p>
  </section>
</template>

<script>

export default {
  name: 'VideoResultSection',
  props: {
    heading: String,
    description: String,
  },
};
</script>
