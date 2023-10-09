



<template>
  <div id="app">
    <input v-model="city" placeholder="Şehir adını girin" />
    <BButton @click="getWeather" variant="primary">Sorgula</BButton>
    <WeatherComponent v-if="weatherData" :data="weatherData" />
  </div>
</template>



<script>

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
