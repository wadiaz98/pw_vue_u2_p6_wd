<template>
  <div class="opciones-container">
    <ul>
      <li
        v-for="pokemon in pokemons"
        :key="pokemon.id"
        @click="
          $emit('seleccionPokemon', {
            ident: pokemon.id,
            nomb: pokemon.nombre,
            test: 'Prueba1',
            test2: test3,
          })
        "
      >
        <!-- v-on=@ -->
        <!-- El emit debe enviar al menos un elemento, y usa el nombre, y se usa en eventos -->
        <!-- Como segundo argumento del emit se puede enviar un dato -->
        {{ pokemon.nombre }}
      </li>
    </ul>
    <!-- order list -->
  </div>
</template>

<script>
export default {
  props: {
    pokemons: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      test3: "Segunda prueba",
    };
  },
};
</script>

<style scoped>
.opciones-container {
  display: flex;
  justify-content: center;
}
ul {
  list-style-type: none;
}
li {
  border: 1px solid rgba(0, 0, 0, 0.5);
  border-radius: 5px;
  margin-bottom: 10px;
  width: 200px;
  background: white;
  cursor: pointer;
}
li:hover {
  background: rgba(0, 0, 0, 0.05);
}
</style>