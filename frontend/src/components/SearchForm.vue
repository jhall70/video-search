<template>
<form class="search-form">
  <input
      :value="childSearchTerm"
       @input="$emit('update:childSearchTerm', $event.target.value)"
      placeholder="Search for a video"
  />
  <font-awesome-icon icon="search" />
</form>
</template>

<script>

import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome';

export default {
  name: 'VideoForm',
  components: {
    FontAwesomeIcon,
  },
  props: {
    childSearchTerm: String,
  },
};
</script>
