<template lang="html">

  <li>{{ beer.name }}</li>

</template>

<script>


export default {
    name: 'list-item',
    props: ['beer']

}
</script>

<style lang="css" scoped>

</style>