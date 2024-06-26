<template>
  <div class="container">
    <label>Intentos: {{ intento }}</label>
    <label>Puntos: {{ puntos }}</label>
  </div>
</template>

<script>
export default {
  props: {
    intento: Number,
    total: {
      type: Boolean,
      required: true,
      default: false,
    },
  },
  data() {
    return {
      puntos: 0,
      intentos: 0,
    };
  },
  methods: {
    asignarPuntos() {
      let puntos = 0;
      if (this.total) {
        switch (this.intento) {
          case 1:
            this.puntos = this.puntos + 10;
            break;
          case 2:
            this.puntos = this.puntos + 8;
            break;
          case 3:
            this.puntos = this.puntos + 5;
            break;
          case 4:
            this.puntos = this.puntos + 3;
            break;
          case 5:
            this.puntos = this.puntos + 2;
            break;
          case 6:
            this.puntos = this.puntos + 1;
            break;
          case 7:
            this.puntos = this.puntos + 0;
            break;
          default:
            break; // Si el intento es mayor a 7, devuelve 0
        }
      }
      return this.puntos;
    },
  },
  computed: {
    asignarPuntos2() {
      if (this.total) {
        switch (this.intento) {
          case 1:
            this.puntos = this.puntos + 10;
            break;
          case 2:
            this.puntos = this.puntos + 8;
            break;
          case 3:
            this.puntos = this.puntos + 5;
            break;
          case 4:
            this.puntos = this.puntos + 3;
            break;
          case 5:
            this.puntos = this.puntos + 2;
            break;
          case 6:
            this.puntos = this.puntos + 1;
            break;
          case 7:
            this.puntos = this.puntos + 0;
            break;
          default:
            break; // Si el intento es mayor a 7, devuelve 0
        }
      }
      return this.puntos;
    },
  },
  watch: {
    intento: "asignarPuntos", // Llamar a asignarPuntos cuando cambie el intento
  },
};
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
label {
  margin: 2px 2px;
}
</style>