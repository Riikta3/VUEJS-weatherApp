<template>
  <div class="container">
    <h1 class="my-4">App météo avec Vue.js</h1>
    <div class="form-group">
      <label for="city">Entrez le nom d'une ville</label>
      <input
        type="text"
        class="form-control"
        name=""
        id="city"
        v-model="requete"
        @keypress.enter="goMeteo"
      />
      <div class="w-75 m-auto mt-5" v-if="temps">
        <h3 class="text-center mb-3">Position: {{ ville }}</h3>
        <div class="card text-center p-5">
          <p class="text-affichage">Temperature : {{ temperature }}</p>
          <p class="text-affichage">Temps : {{ temps }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Meteo",
  data() {
    return {
      requete: "",
      temperature: undefined,
      temps: undefined,
      ville: undefined,
      api_code: process.env.VUE_APP_WEATHER_APIKEY,
      url_recherche: "https://api.openweathermap.org/data/2.5/weather?",
    };
  },
  methods: {
    goMeteo() {
      axios
        .get(
          `${this.url_recherche}q=${this.requete}&units=metric&appid=${this.api_code}&lang=fr`
        )
        .then((res) => {
          this.ville = res.data.name;
          this.temperature = Math.round(res.data.main.temp);
          this.temps = res.data.weather[0].description;
        });
      this.requete = "";
    },
  },
};
</script>

<style>
.text-affichage {
  font-size: 30px;
  font-weight: 200;
  line-height: 1.2;
}
</style>