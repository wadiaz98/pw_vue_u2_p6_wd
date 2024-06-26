<template>
  <h1 v-if="!pokemonCorrecto">Por favor espere.......</h1>
  <div v-else>
    <h1>Selecciona el Pokemon correcto</h1>
    <HUD :intento="intentoActual" :soluciono="solucionoEnIntento" />
    <PokemonImagen :idPokemon="pokemonCorrecto.id" :mostrarPokemon="mostrar" />
    <PokemonOpciones
      v-show="!ocultarOpciones"
      :pokemons="arreglo"
      @seleccionPokemon="revisarRespuesta($event)"
    />
    <div class="mensajes">
      <div class="final_felicitaciones" v-show="ocultarOpciones">
        <h2>Felicitaciones el pokemon es {{ pokemonCorrecto.nombre }}</h2>
        <button @click="siguientePokemon">Siguiente Pokemon</button>
      </div>
      <div class="final_incorrecto"></div>
      <h2 v-show="!ocultarOpciones && sigaIntentando">
        Pokemon incorrecto siga intentando
      </h2>
    </div>
  </div>
  <!-- <div>{{ cargaInicial() }}</div> -->
</template>

<script>
import PokemonImagen from "../components/PokemonImagen.vue";
import PokemonOpciones from "../components/PokemonOpciones.vue";
import Deber from "../components/Deber.vue";
import obtenerPokemonsFachada from "@/clientes/ClientePokemonAPI"; /* Solo para funciones */

export default {
  components: {
    PokemonImagen,
    PokemonOpciones,
    Deber,
  },
  methods: {
    async cargaInicial() {
      const vectorInicial = await obtenerPokemonsFachada(7);
      this.arreglo = vectorInicial;

      const indice = Math.floor(Math.random() * 7);
      this.pokemonCorrecto = this.arreglo[indice];
    },
    revisarRespuesta(dato) {
      this.sumarIntento();

      console.log("Se emitio un evento desde el hijo");
      console.log(dato);

      if (dato.ident === this.pokemonCorrecto.id) {
        this.mostrar = true;
        /* Ocultar las otras opciones, y presentar un mensaje que diga felicitaciones y el nombre del pokemon */
        this.ocultarOpciones = true;

        //para el HUB
        this.solucionoEnIntento = true;
      } else {
        console.log("ERRORrr.....");
        this.sigaIntentando = true;
      }
    },
    sumarIntento() {
      this.intentoActual += 1;
    },
    async siguientePokemon() {
      this.arreglo = [];
      this.mostrar = false;
      this.ocultarOpciones = false;
      this.sigaIntentando = false;
      this.intentoActual = 0;
      this.solucionoEnIntento = false;
      await this.cargaInicial();
    },
  },
  data() {
    return {
      arreglo: [],
      pokemonCorrecto: null,
      /* llamar: this.cargaInicial(), Esto se puede hacer pero no se recomienda */
      mostrar: false,
      ocultarOpciones: false,
      sigaIntentando: false,
      intentoActual: 0,
      solucionoEnIntento: false,
    };
  },
  mounted() {
    this.cargaInicial();
  } /* se dispara cuando se incia pa pagina web */,
};
</script>

<style scope></style>