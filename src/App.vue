<template lang="html">
  <main>
    <h1>BrewDog API</h1>

  </main>
</template>

<script>
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
}
}
</script>

<style>

</style>
