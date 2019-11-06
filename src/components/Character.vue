<template>
  <button class="character" @click="chooseCharacter(character.id)">
    <img :src="character.image" />
    <h3>{{ character.name }}</h3>
  </button>
</template>

<script>
export default {
  props: ["character"],
  methods: {
    chooseCharacter(id) {
      this.$emit("characterChosen", { id });
    }
  }
};
</script>

<style scoped>
.character {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  flex: 1;
  position: relative;
  margin: 1px;
  cursor: pointer;
  border: 0;
  background-color: black;
}

.character img {
  object-fit: cover;
}

.character h3 {
  text-align: center;
  margin: 0px auto;
  padding: 2px 0 4px;
  width: 100%;
  font-weight: 400;
  position: absolute;
  bottom: 0;
  color: #fff;
  background-color: rgba(0, 0, 0, 0.5);
}
</style>
