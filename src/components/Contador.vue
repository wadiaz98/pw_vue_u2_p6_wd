<template>
  <h2>{{presentar}}</h2>
  <p>{{ numero }} <sup>2</sup> = {{ calcular }}</p>
  <div>
    <button @click="incrementar">+1</button>
    <button @click="disminuir">-1</button>
  </div>

</template>

<script>
export default {
  /* Forma básica de declarar un props */
  /* props:['titulo', 'num'], */
  props:{
    titulo:String,
    num: {
      type: Number,
      required: true,
      default: 2,
      validator(value){
        return value >= 0
      }
    },
    
  },

  data() {
    return {
      numero: this.num,
    }
  },
  methods: {
    calcularCuadrado() {
      console.log('Ingresó al método');
      return this.numero * this.numero;
    },
    calcularCuadrado2(num1, num2) {
      console.log('Ingresó al método2');
      return num1 * num2;
    },
    incrementar() {
      this.numero++;
    },
    disminuir() {
      this.numero--;
    }
  },
  computed: {
    calcular() {
      console.log('Ingresó a la propiedad computada');
      return this.numero * this.numero;
    },
    presentar(){
      if(this.titulo!== undefined){
        return this.titulo
      }else{
        return 'Contador';
      }
    }
  }
}
</script>

<style scoped>
  button{
    background: #64B687;
    border-radius: 5PX;
    border: 1px solid white;
    color: white;
    margin: 10px 5px;
    padding: 5px 15px;
    cursor: pointer;
  }
  button:hover{
    background: #5aa67b;
  }
</style>