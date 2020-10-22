<template lang="html">
  <main>
    <h1>BrewDog API</h1>
      <beer-list :beers='beers'></beer-list>
      
  </main>
</template>

<script>

import BeerList from './components/BeerList.vue';
import BeerDetail from './components/BeerDetail.vue';
import { eventBus } from '@/main.js';


export default {
  name: 'app',
  data(){
    return {
      beers: [],
      selectedBeer: null,
      favouriteBeers: []
  };
},
mounted() {
  fetch('https://api.punkapi.com/v2/beers')
  .then(res => res.json())
  .then(beers => this.beers = beers);

  eventBus.$on('beer-selected', (beer) => {
    this.selectedBeer = beer
  })
},
components: {
  "beer-list": BeerList,
  "beer-detail"
},

}
</script>

<style>

</style>
