<template>
  <img v-if="image" :src="image" alt="Not found" />

  <div class="oscuro"></div>
  <div class="pregunta_container">
    <input v-model="pregunta" type="text" placeholder="Hazme una pregunta " />
    <p>Recuerda terminar las pregunta con (?)</p>
    <div v-show="mensaje" class="respuesta">
      <h2>{{ pregunta }}</h2>
      <h1>{{ respuesta === 'yes'? "SI":"NO!" }}</h1>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      respuesta:null,
      pregunta: null,
      image:null,
      mensaje:false,
    };
  },
  watch: {
    pregunta(value, oldValue) {
      this.mensaje = false;
      console.log({ value, oldValue });
      if (!value.includes("?")) {
        this.respuesta = null;
        
        return; /* Salgase del observador */
      }
      //Consumir el API para obtener la respuesta
      this.getResponse();
      this.mensaje = true;
    },
  },
  methods: {
    async getResponse() {
      this.respuesta = "Pensando......"
      const data = await fetch("https://yesno.wtf/api").then((r) => r.json());
      this.respuesta = data.answer;
      this.image = data.image;
    },
  },
};
</script>

<style scoped>
img,
.oscuro {
  max-width: 100%;
  height: 100vh;
  max-height: 100%;
  width: 100vw;
  position: fixed; /* Irrespeta la posición poniendole sobre los demas */
  top: 0px;
  left: 0px;
}

.oscuro {
  background-color: rgba(0, 0, 0, 0.5);
  /* 0.0 full transparente y 1.0 full opaco */
}

.pregunta_container {
  position: relative;
}

p,
h1,
h2 {
  color: white;
}
input {
  margin-top: 70px;
  width: 260px;
  padding: 10px 15px;
  border: none;
  border-radius: 5px;
}

input:focus {
  outline: none;
}

.respuesta {
  margin-top: 100px;
}

P {
  font-size: 25px;
  margin-top: 0px;
}
</style>