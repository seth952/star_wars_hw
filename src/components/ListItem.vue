<template>



  
 <li>{{character.name}}
 <button v-on:click="handleClick" type="button">More Information</button>
 <button v-on:click="addFavourite" type="button">Add to favourites</button>

 </li>


</template>
<script>
import { eventBus } from '../main.js'
export default {
  name: 'list-item',
  data(){
    return {
      favouriteCharacter: this.beer
    }
  },
  methods: {
    handleClick(){
      eventBus.$emit('select-character', this.character);
    },
    addFavourite(){
      this.favouriteCharacter = this.character;
      eventBus.$emit('add-favourite', this.character)
      this.favouriteCharacter = null;
      console.log('click');
}
  },
  props: ['character']
}
</script>
<style lang="css" scoped>
</style>
