<template>
  <div>


  <h1>Star Wars</h1>

    <character-list :characters="characters"/>
    <character-details :character="selectedCharacter"/>
    <h1>Favorite</h1>
     <character-list :characters="favouriteCharacter"/>
  </div>

</template>
<script>
import CharacterList from './components/CharacterList.vue';
import { eventBus } from './main.js';
import CharacterDetail from './components/CharacterDetail.vue';

export default {
  name: 'app',
  data(){
   return {
     characters: [],
     selectedCharacter: null,
     favouriteCharacter: []
   }
 },
  mounted() {
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then(characters => this.characters = characters)

    eventBus.$on('select-beer', (beer) => {
         this.selectedBeer = beer
       }),
       eventBus.$on('add-favourite', (character) => {
         console.log('recieved', character);
         if (!this.favouriteCharacter.includes(character)){
           this.favouriteCharacter.push(character)
         }
       })


  },
  components: {
    "character-list": CharacterList,
    "character-details": CharacterDetail
  }

}
</script>
<style lang="css" scoped>
</style>
