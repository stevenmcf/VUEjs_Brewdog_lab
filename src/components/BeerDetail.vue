<template lang='html'>
  <div v-if='beer'>
      <h3>{{ beer.name }}</h3>
      <p>{{ beer.abv }}</p>
      <p> {{ beer.tagline }}</p>
      <p>{{ beer.image_url }}</p>

  </div>
</template>

<script>

import { eventBus } from '../main.js';

export default {
    name: 'beer-detail',
    props: ['beer']
}

</script>

<style lang='css' scoped>

</style>