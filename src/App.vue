<template lang="html">
  <main>
    <header>
      <h1>BrewDog API</h1>
    </header>
      <section class="main-container">
      <beer-list :beers='beers'></beer-list>
      
      <beer-detail :beer='selectedBeer' :favouriteBeers='favouriteBeers'></beer-detail>
      
      
      <favourite-beers :favouriteBeers='favouriteBeers'></favourite-beers>
      <!-- <button v-if="favouriteBeers.includes(selectedBeer)" v-on:click="deleteFromFavourites">You now hate this beer</button> -->
      </section>
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

    eventBus.$on('favourite-selected', (beer) => {
      this.favouriteBeers.unshift(beer)
    })

    },
  
  methods: {
    // addToFavourites: function() {
    //   this.favouriteBeers.push(this.selectedBeer)
    // }
    // // deleteFromFavourites: function() {
    //   this.favouriteBeers.unshift(this.)
    // }
  },
      
  }
  
</script>

<style lang='css' scoped>

main {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  font-size: 10pt;
  margin: 0px;
  padding: 0px;
  height: 80%;
}

html {
  margin: 0px;
  height: max-content;
}

header {
  margin: 0%;
  background-color: black;
  padding-top: 15px;
  color: white;
  text-align: center;
  font-size: 14pt;
}

.main-container {
  display: flex;
  justify-content: space-between;
}
/* 
ul {
  display: flex;
  justify-content: flex-start;
  flex-wrap: wrap;
  padding:20px;
  margin: 0;
}
 */


</style>
