<template lang='html'>
  <article id="beer_detail" v-if='beer'>
      <button v-if="!favouriteBeers.includes(beer)" v-on:click='handleClick' :value="beer">Add your favourite Brewdog beer</button>
      <h3>Beer Name: {{ beer.name }}</h3>
      <p>Strength: {{ beer.abv }}.abv</p>
      <p>Whats it all about: {{ beer.tagline }}</p>
      <img :src="beer.image_url" alt="beer image" height="30%" width="auto" margin-right="auto" margin-left="auto">
      
  </article>
</template>

<script>
import { eventBus } from '../main.js';

export default {
    name: 'beer-detail',
    props: ['beer', 'favouriteBeers'],

    methods: {
        handleClick () {
            eventBus.$emit('favourite-selected', this.beer)
        }
    }
}
</script>

<style lang='css' scoped>

#beer_detail {
    border: 2px solid blue;
    border-radius: 8px;
    padding: 16px;
    background-color: cadetblue;
    width: 27%;
    max-height: 100vh;

}



</style>