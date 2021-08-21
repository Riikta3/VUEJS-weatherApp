<template>
  <div id="app">
    <meteo />
  </div>
</template>

<script>
import Meteo from "./components/Meteo.vue";
export default {
  name: "App",
  components: {
    meteo: Meteo,
  },
};
</script>

<style>
body {
  height: 100vh;
  width: 100vw;
  background: #e0eafc;
  background: -webkit-linear-gradient(to right, #cfdef3, #e0eafc);
  background: linear-gradient(to top, #cfdef3, #e0eafc);
}
</style>
