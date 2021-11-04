<template>
    <div class="info">
        <div class="place-date">
            <div class="place">
                 <h3>{{data.city + ' - ' + data.country}}</h3>
            </div>
            <div class="date">
                <h3>{{data.currentDate}}</h3>
            </div>
        </div>
        <div class="icon-temp-condition">
            <div class="icon-container">
                <img :src="data.icon" alt="icon"/>
            </div>
            <div class="temp-condition">
                <h2 id="temp">{{data.tempC}}</h2>
                <h3>{{data.condition}}</h3>
            </div>
        </div>
        <div class="humidity-wind">
            <h3>Humidity: {{data.humidity}}</h3>
            <h3>Wind: {{data.wind}}</h3>
        </div>
        <div class="feels-like">
            <h3>Feels like: {{data.feelsLikeC}}</h3>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        data: {
            required: true
        }
    }
}
</script>