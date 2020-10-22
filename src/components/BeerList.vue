<template lang='html'>
  <body>
      <ul>
          <list-item v-for="(beer, id) in beers" :key="beer.id" :beer="beer"></list-item>
      </ul>
  </body>
</template>

<script>
export default {
    name: "beer-list",
    props: ['beers'],
}
</script>

<style lang='css'>

</style>