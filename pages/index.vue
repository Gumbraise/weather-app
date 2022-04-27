<template>
  <div class="text-white p-2">
    <div
      class="container max-w-screen-sm bg-gradient-to-b from-weather-lightblue to-weather-darkblue mx-auto p-8 rounded-3xl shadow-lg">
      <header class="text-center">
        <h1 class="text-2xl font-bold">{{ api.name }}</h1>
      </header>
      <div class="divide-y-2 space-y-8 divide-opacity-10 divide-white">
        <div class="text-center">
          <img src="http://openweathermap.org/img/wn/10d@4x.png" alt="" class="w-full">
          <h2 class="text-9xl font-bold">{{ temp }}°</h2>
          <h2 class="text-2xl">{{ weather.main }}</h2>
          <h2 class="text-sm font-white opacity-50 capitalize">{{ getDate() }}</h2>
        </div>
        <div class="text-center grid grid-cols-3">
          <div>
            <img src="http://openweathermap.org/img/wn/10d@2x.png" alt="">
            <p class="text-sm font-white">13km/h</p>
            <p class="text-sm font-white opacity-50">Wind</p>
          </div>
          <div>
            <img src="http://openweathermap.org/img/wn/10d@2x.png" alt="">
            <p class="text-sm font-white">13km/h</p>
            <p class="text-sm font-white opacity-50">Wind</p>
          </div>
          <div>
            <img src="http://openweathermap.org/img/wn/10d@2x.png" alt="">
            <p class="text-sm font-white">13km/h</p>
            <p class="text-sm font-white opacity-50">Wind</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import moment from 'moment';

export default {
  name: 'IndexPage',
  data() {
    return {
      api: {},
      main: {},
      weather: {},
      temp: 0,
    }
  },
  created() {
    this.getWeather();
  },
  methods: {
    async getWeather() {
      const api = await this.$axios.$get(`?q=saint-amand&units=metric&appid=7c34a116703ac59887e21cfc5260847c`)

      this.api = api
      this.main = api.main
      this.temp = (api.main.temp).toFixed(0)
      this.weather = api.weather[0]
    },

    getDate() {
      return moment().locale('fr').format('dddd DD MMMM')
    }
  }
}
</script>

<style lang="scss">
html, body {
  @apply bg-weather-dark;
}
</style>
