<template lang='html'>
  <article id="beer_detail" v-if='beer'>
      <h3>Beer Name: {{ beer.name }}</h3>
      <p>Strength: {{ beer.abv }}</p>
      <p>Whats it all about: {{ beer.tagline }}</p>
      <img :src="beer.image_url" alt="beer image">
  </article>
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