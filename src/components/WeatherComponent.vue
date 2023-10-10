<template>
    <div>
        <h2>{{ data.name }}</h2>
        <p>Sıcaklık: {{ data.main.temp }}°C</p>
        <p>Açıklama: {{ data.weather[0].description }}</p>
    </div>
</template>

<script>
export default {
    name: 'WeatherComponent',
    props: {
        data: Object
    }
};
</script>