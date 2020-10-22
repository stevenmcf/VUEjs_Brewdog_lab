<template lang='html'>
  <article id="beer_list">
      <h2>Choose your BrewDog</h2>
      <ul>
          <list-item v-for="(beer, id) in beers" :key="beer.id" :beer="beer"></list-item>
      </ul>
  </article>
</template>

<script>
import BeerListItem from './BeerListItem.vue'

export default {
    name: "beer-list",
    props: ['beers'],
    components: {
        "list-item": BeerListItem
    }
}
</script>

<style lang='css'>

#beer_list {
    border: 2px solid blue;
    border-radius: 8px;
    padding: 16px;
    background-color: cadetblue;
    width: 27%;
  
}


</style>