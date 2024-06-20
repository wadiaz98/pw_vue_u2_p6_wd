<template>
  <div class="imagen-container">
    <img
      v-show="mostrar"
      class="oculta"
      src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/94.svg"
      alt="Not Found"
    />
    <img
      v-show="!mostrar"
      class="ver"
      src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/94.svg"
      alt="Not Found"
    />
  </div>
</template>

<script>
export default {
  data() {
    return {
      mostrar: true,
    };
  },
};
</script>

<style scoped>
.imagen-container{
    width: 250px;
    height: 250px;
}
.oculta {
  filter: brightness(0);
}
img {
  width: 250;
  height: 250px;
  position: absolute;
  right: 43%;
}
</style>