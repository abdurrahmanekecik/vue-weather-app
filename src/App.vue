<template>
  <div id="app">
    <BForm>
      <BFormGroup id="input-group-2" label="City Name:" label-for="input-2">
        <BFormInput id="input-2" class="mb-2 me-sm-2 mb-sm-0" v-model="city" placeholder="City Name Enter" required />
      </BFormGroup>
      <BButton @click="getWeather" variant="primary">Search</BButton>
      <WeatherComponent v-if="weatherData" :data="weatherData" />
    </BForm>
  </div>
</template>

<script>
import WeatherComponent from './components/WeatherComponent.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    WeatherComponent
  },
  data() {
    return {
      city: '',
      weatherData: null
    };
  },
  methods: {
    async getWeather(event) {
      event.preventDefault();

      try {
        console.log(process.env.VUE_APP_API_KEY);
        const response = await axios.get(`https://api.openweathermap.org/data/2.5/weather?zip=${this.city},US&appid={${process.env.VUE_APP_API_KEY}}&units=imperial`)
        this.weatherData = response.data;
      } catch (error) {
        console.error("Hava durumu bilgisi alınırken bir hata oluştu:", error);
      }
    }
  }
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
