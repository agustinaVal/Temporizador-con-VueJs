<template>
  <div id="app">
    <h1>
      {{ contadorMin < 10 ? '0' + contadorMin : contadorMin }}:{{
      contadorSeg < 10 ? '0' + contadorSeg : contadorSeg
      }}
      min/seg
    </h1>
    <div class="botones">
      <button @click="iniciar(3)">3 segs</button>
      <button @click="iniciar(60)">1 min</button>
      <button @click="iniciar(180)">2 min</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Contador",

  data() {
    return {
      contadorMin: 0,
      contador2Min: 0,
      contadorSeg: 0,
      miIntervalo: null
    };
  },

  methods: {
    iniciar(tiempo) {
      this.contadorSeg = tiempo;
      clearInterval(this.miIntervalo);
      this.miIntervalo = setInterval(() => {
        this.contadorSeg > 0 ? this.contadorSeg-- : false;
        console.log("Soy el intervalo >:-)");
      }, 1000);
      setTimeout(() => {
        clearInterval(this.miIntervalo);
      }, (tiempo + 1) * 1000);
    }
  }
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;

  ul {
    li {
      color: blue;
    }
  }
  button {
    padding: 20px;
    background-color: coral;
    color: white;
    font-weight: bold;
    border: 1px solid coral;
    border-radius: 5px;
    margin-right: 5px;
  }
}
</style>
