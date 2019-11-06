<template>
  <div class="selected-character" v-if="character">
    <h4>Your Selected Character</h4>
    {{ character.name }}
  </div>
</template>

<script>
export default {
  props: ["character"]
};
</script>

<style scoped>
.selected-character {
  color: #fff;
  text-align: center;
  width: 100%;
  padding: 10px 0 40px;
}

.selected-character h4 {
  margin: 0 0 10px;
}
</style>
