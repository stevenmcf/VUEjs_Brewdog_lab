<template lang='html'>
  <body>
      <ul>
          <list-item v-for="(beer, id) in beers" :key="beer.id" :beer="beer"></list-item>
      </ul>
  </body>
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

</style>