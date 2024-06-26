<template>
    <div class="weather-container">
      <div class="search-bar">
        <input
          type="text"
          v-model="city"
          placeholder="Enter City Name"
          @keyup.enter="fetchWeather"
          class="city-input"
        />
        <button @click="fetchWeather" class="search-button">Search</button>
      </div>
      <div v-if="weather.main" class="weather-info">
        <h2>{{ city }}</h2>
        <div :class="`weather-icon icon-${weather.main.toLowerCase()}`"></div>
        <div class="description">{{ weatherDescription }}</div>
        <div class="temperature">{{ temperature }}°C</div>
      </div>
      <div v-else class="no-data">No weather data available.</div>
    </div>
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
      weatherDescription() {
        return this.weather.description
          ? this.weather.description.charAt(0).toUpperCase() + this.weather.description.slice(1)
          : '';
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
  .weather-container {
    max-width: 600px;
    margin: 50px auto;
    padding: 30px;
    background-color: #e3f2fd;
    border-radius: 16px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
    font-family: 'Arial', sans-serif;
    text-align: center;
  }
  
  .search-bar {
    display: flex;
    justify-content: center;
    margin-bottom: 20px;
  }
  
  .city-input {
    padding: 12px;
    border: 1px solid #ddd;
    border-radius: 10px 0 0 10px;
    width: 70%;
    font-size: 18px;
    outline: none;
  }
  
  .search-button {
    padding: 12px 20px;
    border: none;
    border-radius: 0 10px 10px 0;
    background-color: #0288d1;
    color: white;
    cursor: pointer;
  }
  
  .search-button:hover {
    background-color: #0277bd;
  }
  
  .weather-info {
    background: linear-gradient(to top, #4caf50, #81c784);
    padding: 25px;
    border-radius: 16px;
    color: #fff;
    margin-top: 20px;
  }
  
  .weather-icon {
    margin: 20px 0;
    font-size: 80px;
    position: relative;
  }
  
  .icon-sunny::before {
    content: "☀️";
    animation: spin 5s linear infinite;
    font-size: 5rem;
  }
  
  .icon-cloudy::before {
    content: "☁️";
    font-size: 5rem;
    animation: drift 4s ease-in-out infinite;
  }
  
  .icon-rainy::before {
    content: "🌧️";
    font-size: 5rem;
    animation: rain 1s linear infinite;
  }
  
  .icon-snowy::before {
    content: "❄️";
    font-size: 5rem;
    animation: snow 1.5s linear infinite;
  }
  
  .icon-thunderstorm::before {
    content: "🌩️";
    font-size: 5rem;
    animation: flash 0.6s linear infinite;
  }
  
  .icon-drizzle::before {
    content: "🌦️";
    font-size: 5rem;
    animation: drizzle 1.2s linear infinite;
  }
  
  .icon-default::before {
    content: "🌥️";
    font-size: 5rem;
  }
  
  .description {
    font-size: 20px;
    margin: 10px 0;
  }
  
  .temperature {
    font-size: 28px;
    font-weight: bold;
  }
  
  .no-data {
    font-size: 22px;
    color: #777;
    margin-top: 30px;
  }
  
  @keyframes spin {
    to {
      transform: rotate(360deg);
    }
  }
  
  @keyframes drift {
    0%, 100% {
      transform: translateX(0);
    }
    50% {
      transform: translateX(10px);
    }
  }
  
  @keyframes rain {
    0%, 100% {
      transform: translateY(0);
    }
    50% {
      transform: translateY(10px);
    }
  }
  
  @keyframes snow {
    0%, 100% {
      transform: translateY(0);
    }
    50% {
      transform: translateY(5px);
    }
  }
  
  @keyframes flash {
    0%, 100% {
      opacity: 1;
    }
    50% {
      opacity: 0.5;
    }
  }
  
  @keyframes drizzle {
    0%, 100% {
      transform: translateY(0);
    }
    50% {
      transform: translateY(7px);
    }
  }
  </style>
  