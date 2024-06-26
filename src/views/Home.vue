<template>
  <q-page class="weather-page">
    <q-card class="weather-card">
      <q-card-section class="weather-header">
        <h1 class="title">Weather Detector</h1>
      </q-card-section>

      <q-card-section class="weather-body">
        <div class="search-bar">
          <input
            type="text"
            v-model="city"
            placeholder="Enter City Name"
            @keyup.enter="fetchWeather"
            class="city-input"
          />
          <q-btn @click="fetchWeather" color="primary" icon="search" round dense flat class="search-button" />
        </div>

        <div v-if="weather.main" class="weather-info">
          <div class="weather-icon">
            <i :class="weatherIcon"></i>
          </div>
          <div class="weather-details">
            <h2 class="temperature">{{ temperature }}°C</h2>
            <div class="description">{{ weatherDescription }}</div>
            <h3 class="city">{{ city }}</h3>
          </div>
        </div>
        <div v-else class="no-data">No weather data available.</div>
      </q-card-section>
    </q-card>
  </q-page>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      city: 'Jakarta',
      weather: {},
      temperature: null,
    };
  },
  computed: {
    weatherIcon() {
      switch (this.weather.main) {
        case 'Clear': return 'fas fa-sun';
        case 'Clouds': return 'fas fa-cloud';
        case 'Rain': return 'fas fa-cloud-rain';
        case 'Snow': return 'fas fa-snowflake';
        case 'Thunderstorm': return 'fas fa-bolt';
        case 'Drizzle': return 'fas fa-cloud-showers-heavy';
        default: return 'fas fa-question';
      }
    },
    weatherDescription() {
      return this.weather.description ? this.weather.description.charAt(0).toUpperCase() + this.weather.description.slice(1) : '';
    }
  },
  methods: {
    async fetchWeather() {
      if (!this.city) return;
      const API_KEY = '4d1db2666da951482ad444c5f52dc755';
      try {
        const response = await axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&appid=${API_KEY}&units=metric`);
        this.weather = response.data.weather[0];
        this.temperature = response.data.main.temp;
      } catch (error) {
        console.error("Error fetching weather data:", error);
        alert("City not found or network error.");
      }
    }
  },
  mounted() {
    this.fetchWeather();
  }
};
</script>

<style scoped>
.weather-page {
  background-color: #34495e;
  color: #fff;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.weather-card {
  background-color: #2c3e50;
  color: #fff;
  border-radius: 20px;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
  width: 80%;
  max-width: 400px;
}

.weather-header {
  background-color: #3498db;
  padding: 20px;
  border-top-left-radius: 20px;
  border-top-right-radius: 20px;
}

.title {
  font-size: 2em;
  font-weight: bold;
  text-align: center;
}

.weather-body {
  padding: 20px;
}

.search-bar {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 20px;
}

.city-input {
  flex: 1;
  padding: 10px;
  border: none;
  border-radius: 10px 0 0 10px;
  font-size: 16px;
}

.search-button {
  border-radius: 0 10px 10px 0;
}

.weather-info {
  display: flex;
  align-items: center;
  justify-content: space-around;
}

.weather-icon {
  font-size: 4em;
}

.weather-details {
  text-align: center;
}

.temperature {
  font-size: 2.5em;
  font-weight: bold;
  margin-bottom: 5px;
}

.description {
  font-size: 1.5em;
  text-transform: capitalize;
}

.city {
  font-size: 1.2em;
  margin-top: 10px;
}

.no-data {
  text-align: center;
  font-size: 1.2em;
  margin-top: 20px;
}
</style>
