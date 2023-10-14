<template>
    <br>
    <div>
        <h2>{{ data.name }}</h2>
        <p>Sıcaklık: {{ kelvinToCelsius(data.main.temp) }}°C</p>
        <p>Açıklama: {{ data.weather[0].description }}</p>
    </div>
</template>

<script>
export default {
    name: 'WeatherComponent',
    props: {
        data: Object
    },
    methods: {
        kelvinToCelsius(kelvin) {
            return (kelvin - 273.15).toFixed(2);
        }
    }
};
</script>