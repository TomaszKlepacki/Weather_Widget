
<template>
  <div class="home">
    <main>

      <h1 class="heading">Widget pogodowy</h1>

      <div class="search">
        <input
          type="text"
          class="search-bar"
          placeholder="Szukaj..."
          v-model="query"
          @keypress="fetchWeather"
        />

        <div class="fa-3x">
          <button type="button" class="button" @click="get">
            <i class="fa-solid fa-magnifying-glass"></i>
            Wyszukaj
          </button>
        </div>
      </div>

      <div class="weather-wrap" v-if="typeof weather.main != 'undefined'">
        <div class="location-box">
          <div class="location">
            {{ weather.name }}, {{ weather.sys.country }}
          </div>
          <div class="date">{{ todaysDate() }}</div>
        </div>

        <table class="content-table">
          <thead>
            <tr>
              <th>Temperatura</th>
              <th>{{ Math.round(weather.main.temp) }} °C</th>
            </tr>
          </thead>

          <tbody>
            <tr class="active-row">
              <td>Opis</td>
              <td>{{ weather.weather[0].description }}</td>
            </tr>

            <tr class="active-row">
              <td>Temp. Min:</td>
              <td>{{ Math.round(weather.main.temp_min) }} °C</td>
            </tr>

            <tr class="active-row">
              <td>Temp. Max:</td>
              <td>{{ Math.round(weather.main.temp_max) }} °C</td>
            </tr>

            <tr class="active-row">
              <td>Ciśnienie atmosferyczne</td>
              <td>{{ Math.round(weather.main.grnd_level) }} hPa</td>
            </tr>

            <tr class="active-row">
              <td>Wilgotność:</td>
              <td>{{ weather.main.humidity }} %</td>
            </tr>

            <tr class="active-row">
              <td>Prędkość wiatru:</td>
              <td>{{ weather.wind.speed }} km/h</td>
            </tr>

            <tr class="active-row">
              <td>Zachmurzenie:</td>
              <td>{{ Math.round(weather.clouds.all) }} %</td>
            </tr>
          </tbody>
        </table>
      </div>
    </main>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      api_key: "2e8feb106cd79be0996756954ea8dcc9",
      url_base: "https://api.openweathermap.org/data/2.5/",
      api_lang: "pl",
      query: "",
      weather: {},
    };
  },


  methods: {
    // a method of finding data from api with enter
    async fetchWeather(e) {
      if (e.key == "Enter") {
        const response = await axios.get(
          `${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}&lang=pl`
        );

        this.setResults(response.data);
      }
    },

    // a method of finding data from api with click on button
    async get() {
      const response = await axios.get(
        `${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}&lang=pl`
      );

      this.setResults(response.data);
    },

    setResults(returnedResponse) {
      this.weather = returnedResponse;
    },

/*
// unfinished code with geolocation

    geolocation() {
      navigator.geolocation.getCurrentPosition(this.buildUrl, this.geoError);
    },
    buildUrl(position) {
      const lat = position.coords.latitude;
      const lon = position.coords.longitude;

      this.getWeather(
        this.url_base + "&lat=" + lat + "&lon=" + lon + this.api_key
      );
    },
    geoError(error) {
      this.getWeather(API + "&lat=0&lon=0" + KEY);
    },

*/

// Current date

    todaysDate() {
      const months = [
        "Styczeń",
        "Luty",
        "Marzec",
        "Kwiecień",
        "Maj",
        "Czerwiec",
        "Lipiec",
        "Sierpień",
        "Wrzesień",
        "Październik",
        "Listopad",
        "Grudzień",
      ];
      const days = [
        "Niedziela",
        "Poniedziałek",
        "Wtorek",
        "Środa",
        "Czwartek",
        "Piątek",
        "Sobota",
      ];

      const d = new Date();
      const month = months[d.getMonth()];
      const day = days[d.getDay()];
      const date = d.getDate();
      const year = d.getFullYear();
      return `${month} ${date} ${day} ${year}`;
    },
  },
};
</script>