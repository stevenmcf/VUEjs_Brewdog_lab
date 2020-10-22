<template lang="html">
  <main>
    <header>
      <h1>BrewDog API</h1>
    </header>
      
      <beer-list :beers='beers'></beer-list>
      <button v-if="!favouriteBeers.includes(selectedBeer)" v-on:click="addToFavourites">Add to favourites!</button>
      
      <beer-detail :beer='selectedBeer'></beer-detail>
      
      
      <favourite-beers :favouriteBeers='favouriteBeers'></favourite-beers>
      <!-- <button v-if="favouriteBeers.includes(selectedBeer)" v-on:click="deleteFromFavourites">You now hate this beer</button> -->
  </main>
</template>

<script>

import BeerList from './components/BeerList.vue';
import BeerDetail from './components/BeerDetail.vue';
import FavouriteBeers from './components/FavouriteBeers.vue'
import { eventBus } from './main.js';


export default {
  name: 'app',
  data(){
    return {
      beers: [],
      selectedBeer: null,
      favouriteBeers: []
    };
  },

   components: {
      "beer-list": BeerList,
      "beer-detail": BeerDetail,
      "favourite-beers": FavouriteBeers
    },
  
  mounted() {
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then(beers => this.beers = beers);

    eventBus.$on('beer-selected', (beer) => {
      this.selectedBeer = beer
      console.log("BEER BEER:", this.selectedBeer);
    })

    },
  
  methods: {
    addToFavourites: function() {
      this.favouriteBeers.push(this.selectedBeer)
    }
    // deleteFromFavourites: function() {
    //   this.favouriteBeers.unshift(this.)
    // }
  },
      
  }
  
</script>

<style lang='css' scoped>

main {
  margin: 0px;
  padding: 0px;
  cursor: pointer;
}

header {
  margin: 0%;
  background-color: black;
  padding-top: 50px;
  color: blue;
  font-size: 40px;
}

ul {
  display: flex;
  justify-content: flex-start;
  flex-wrap: wrap;
  padding:20px;
  margin: 0;
}



</style>
