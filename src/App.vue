
<template>
  <div id="app">
    <BForm>
      <BFormGroup id="input-group-2" label="City Name:" label-for="input-2">
        <BFormInput id="input-2" class="mb-2 me-sm-2 mb-sm-0" v-model="city" placeholder="🔍 City Name Enter" required />
        <!-- Arama ikonu ekledik -->
      </BFormGroup>
      <BButton @click="getWeather">
        <span class="icon">&#x1F50D;</span> <!-- Basit bir arama ikonu -->
        Search
      </BButton>
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
        const response = await axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${this.city},US&appid=${process.env.VUE_APP_API_KEY}`, {
          headers: {
            'Content-Type': 'application/json',
          }
        });
        console.log(response.data);
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
  font-family: 'Roboto', sans-serif;
  /* Modern bir font */
  background-color: #f5f7f9;
  /* Açık mavi arka plan rengi */
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

BForm {
  width: 400px;
  padding: 20px;
  background-color: #ffffff;
  border-radius: 8px;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
}

BFormInput {
  border-radius: 5px;
}

BButton {
  background-color: #3498db;
  /* Parlak mavi buton rengi */
  border: none;
  border-radius: 5px;
  color: #ffffff;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

BButton:hover {
  background-color: #2980b9;
  /* Butonun üstüne geldiğindeki renk */
}

.icon {
  font-size: 24px;
  margin-right: 10px;
}
</style>