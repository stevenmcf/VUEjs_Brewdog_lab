<template lang='html'>
<section id='favourite_beers'>
    <h3>Your Favourite Beers</h3>
    <ul class="list-container">
        <li v-for="favouriteBeer in favouriteBeers">Beer: {{ favouriteBeer.name }}, Strength: {{ favouriteBeer.abv }} <img class="small-beer" :src="favouriteBeer.image_url"></li>
     </ul>
</section>
  
</template>

<script>
export default {
    name: 'favourite-beers',
    props: ['favouriteBeers']
}
</script>

<style lang='css' scoped>

#favourite_beers {
    border: 2px solid blue;
    border-radius: 8px;
    padding: 16px;
  
}

li {
    border: 1px solid black;
    border-radius: 8px;
    padding: 16px;
    width: 25%;
    list-style: none;
    margin: 10px;
}

.list-container {
    display: flex;
    flex-wrap: wrap;
}


.small-beer {

  height: 100px;
}
</style>