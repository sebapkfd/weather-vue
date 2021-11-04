<template>
  <main>
    <div class="title">
      <h1>Weather</h1>
    </div>
    <div class="search-options">
      <form @submit.prevent="fetch">
        <input type="text" placeholder="Search" required v-model="location">
      </form>
    </div>
    <Info :data="result" v-if="result.city"/>
    <Footer />
  </main>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  data() {
    return {
      location: '',
      result: {}
    }
  },
  methods: {
    async fetch() {
      const response = await fetch(
        `https://api.weatherapi.com/v1/current.json?key=a5f5d927bbc64246a51205628200112&q=${this.location}`, {mode: 'cors'})
      const data = await response.json();
      const infoTime = data.location.localtime.split(' ');
      this.result = {
        tempC: `${data.current.temp_c}° C`,
        tempF: `${data.current.temp_f}° F`,
        condition: data.current.condition.text,
        humidity: `${data.current.humidity}%`,
        wind: `${data.current.wind_kph} Km/h`,
        country: data.location.country,
        city: data.location.name,
        feelsLikeC: `${data.current.feelslike_c}° C`,
        feelsLikeF: `${data.current.feelslike_f}° F`,
        icon: `https:${data.current.condition.icon}`,
        currentDate: infoTime[0],
        currentTime: infoTime[1]
      }
    }
  }
})
</script>
