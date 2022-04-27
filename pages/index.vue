<template>
  <div class="text-white p-2">
    <div
      class="container max-w-screen-sm bg-gradient-to-b from-weather-lightblue to-weather-darkblue mx-auto p-4 rounded-3xl shadow-lg">
      <header class="text-center">
        <h1 class="text-2xl font-bold">London</h1>
      </header>
      <div class="text-center">
        <img src="http://openweathermap.org/img/wn/10d@4x.png" alt="" class="w-full">
        <h2 class="text-9xl font-bold">20°</h2>
        <h2 class="text-2xl">Thunderstorm</h2>
        <h2 class="text-sm font-white opacity-50">Mercredi 27 Avril</h2>
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
</template>

<script>
export default {
  name: 'IndexPage',
  data() {
    return {
      weather: {},
    }
  },
  created() {
    this.getWeather();
  },
  methods: {
    async getWeather() {
      const weatherApi = await this.$axios.$get(`?q=saint-amand&appid=7c34a116703ac59887e21cfc5260847c`)
      console.log(weatherApi)
    }
  }
}
</script>
