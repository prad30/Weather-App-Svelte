<script>
export let weatherData;
</script>

<main>
    <div class="weather-data">
        <img src="assets/cloudy.png" alt="Weather" />
        <p class="temperature">{weatherData.temperature}°C</p>
        <p class="city">{weatherData.city}</p>
      </div>
</main>



<style>
.weather-data{
  margin-top: 100px;
  align-items: center;
  display: flex;
  flex-direction: column;
}

.weather-data img{
  width: 250px;
  margin-bottom: 50px;
}

.weather-data p{
  font-size: 50px;
}
</style>