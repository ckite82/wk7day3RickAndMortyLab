<template>
  <div id="app">
    <h1>Characters</h1>
    <div class="main-container">
      <characters-list :characters="characters"></characters-list>
      <character-detail :character='selectedCharacter'></character-detail>

    </div>
  </div>
</template>

<script>
import CharactersList from './components/CharactersList.vue';
import CharacterSelect from './components/CharacterSelect.vue';
import CharacterDetails from './components/CharacterDetails.vue';
import {eventBus} from './main';

export default {
  name: 'App',
  data(){
    return {
      characters: [],
      selectedCharacter: null
    };
  },
  mounted(){
    fetch('https://rickandmortyapi.com/api/character/')
    .then(res => res.json())
    .then(characters => this.characters = characters.results)

    eventBus.$on('character-selected', (character) => {
      this.selectedCharacter = character;
    })
  },
  components: {
  "characters-list": CharactersList,
  "character-detail": CharacterDetails
  }
}
</script>

<style>
  .main-container {
    display: flex;
    justify-content: space-between;
  }
</style>
