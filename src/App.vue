<template>
  <div id="app">
    <Escena
      class="w-50"
      :cielo="localizacionActual.cielo"
      :navegadores="localizacionActual.navegadores"
      :cielos="cielos"
      @cambiar="cambiar"
      :video="localizacionActual.video"
      :informacion="localizacionActual.informacion"
    />
  </div>
</template>

<script>
import Escena from "./components/Escena.vue";
const cielos = ["huella.jpg", "vistafrontal.jpg"];

const escenas = {
  huella: {
    cielo: "huella.jpg",
    navegadores: [{ posicion: "-9 -3 0", hacia: "vistafrontal" }],
  },
  vistafrontal: {
    cielo: "vistafrontal.jpg",
    navegadores: [{ posicion: "9 -3 -10.5", hacia: "huella" }],
    whatsapp: { posicion: "4 -3 8" },
    video: { posicion: "-8 0 -2", link: "youtube.com" },
    informacion: { posicion: "-8 0 2" },
  },
};

export default {
  name: "App",
  data() {
    return {
      localizacionActual: escenas.huella,
      cielos: cielos,
    };
  },
  components: { Escena },
  methods: {
    cambiar: function (hacia) {
      this.localizacionActual = escenas[hacia];
    },
  },
  mounted() {},
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
