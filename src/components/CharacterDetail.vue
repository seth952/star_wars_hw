<template>
  <div v-if="character">
    <h2>Name: {{character.name}}</h2>
    <!-- <p>Description: {{character.description}}</p>
    <p>ABV: {{character.abv}}%</p> -->
    <!-- <img :src="beer.image_url" alt="" height="300px"> -->
  </div>
</template>
<script>
export default {
  name: "character-details",
  props: ['character']
}
</script>
<style lang="css" scoped>
</style>
