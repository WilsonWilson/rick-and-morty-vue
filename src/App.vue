<template>
  <div class="app">
    <h1>Rick and Morty Characters</h1>

    <!-- show the selected character -->
    <SelectedCharacter :character="selectedCharacter" />

    <!-- loop over our characters -->
    <div class="characters">
      <Character
        @characterChosen="chooseCharacter"
        v-for="character in characters"
        :key="character.id"
        :character="character"
      />
    </div>
  </div>
</template>

<script>
import SelectedCharacter from "./components/SelectedCharacter";
import Character from "./components/Character";

export default {
  name: "App",
  components: { SelectedCharacter, Character },
  data() {
    return {
      characters: [],
      selectedCharacter: null
    };
  },
  methods: {
    fetchCharacters() {
      fetch("https://rickandmortyapi.com/api/character/")
        .then(resp => resp.json())
        .then(data => (this.characters = data.results));
    },
    chooseCharacter(event) {
      const character = this.characters.find(c => c.id === event.id);
      this.selectedCharacter = character;
    }
  },
  mounted() {
    this.fetchCharacters();
  }
};
</script>

<style scoped>
h1 {
  text-align: center;
  margin: 20px auto;
  color: #fff;
}
.app {
  margin: 0;
  padding: 0;
  font-family: Arial, Helvetica, sans-serif;
  text-align: center;
}

.characters {
  display: flex;
  max-width: 100vw;
  width: 100vw;
  flex-wrap: wrap;
  padding: 0 5%;
}
</style>
