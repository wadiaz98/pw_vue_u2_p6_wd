<template>
  <div class="pokemon-container">
    <img
      v-show="mostrarPokemon"
      :src="imagenFuente"
      alt="No se pudo visualizar la imagen"
    />

    <img
      v-show="!mostrarPokemon"
      class="oculta-pokemon"
      :src="imagenFuente"
      alt="No se pudo visualizar la imagen"
    />
  </div>
</template>

<script>
export default {
  computed: {
    imagenFuente() {
      return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${this.idPokemon}.svg`;
    },
  },
  data() {
    return {
      mostrar: true,
      urlimagen: "",
    };
  },
  props: {
    idPokemon: {
      type: Number,
      required: true,
    },
    mostrarPokemon: {
      type: Boolean,
      required: true,
      default: true,
    },
  },
};
</script>

<style scoped>
.oculta-pokemon {
  filter: brightness(0);
}

img {
  height: 200px;
  width: 200px;
  position: absolute; /*solapa los elementos en un solo espacio*/
  /*right: 38%;*/
  /*que porcentaje tiene de espacio del borde derecho*/
  margin-left: 50px;
}
.pokemon-container {
  height: 200px;

  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
</style>