<template>
  <div>
    <!-- <Pregunta /> -->

    <PokemonPage />
  </div>
  <!-- <Contador v-bind:num="11 + 1" v-if="false" /> -->
</template>

<script>
/* import Contador from "./components/Contador.vue"; */ /* [1] */
/* import Pregunta from "./components/Pregunta.vue"; */
import PokemonPage from "./pages/PokemonPage.vue";
export default {
  name: "App",
  components: {
    /* [2] */
    /* Pregunta, */
    /*Contador, */
    PokemonPage,
  },
  methods: {
    calcularValor() {
      return 10 + 2;
    },
    async api() {},
  },
  data() {
    return {};
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>