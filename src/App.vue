<template lang="html">
  <main>
    <h1>BrewDog API</h1>
      <beer-list :beers='beers'></beer-list>
  </main>
</template>

<script>
import BeerList from './components/BeerList.vue';


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
  .then(beers => this.beers = beers)
},
components: {
  "beer-list": BeerList
},

}
</script>

<style>

</style>
