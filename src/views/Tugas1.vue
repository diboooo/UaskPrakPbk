<template>
    <q-page class="custom-page">
      <div class="custom-container">
        <q-card flat bordered class="custom-card">
          <q-card-section class="custom-card-section">
            <h2 class="custom-card-title">Tugas 1</h2>
            <div class="custom-card-description">
            </div>
            <div class="custom-card-links">
              <a class="custom-card-link" href="https://agusdiopratama-tugas1-223510070.vercel.app/" target="_blank">Kunjungi Tugas 1</a>
              <router-link to="/" class="custom-card-link">Kembali Ke Beranda</router-link>
            </div>
          </q-card-section>
        </q-card>
      </div>
    </q-page>
  </template>
  
  <script>
  export default {
    name: 'App',
  };
  </script>
  
  <style scoped>
  .custom-page {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100vh;
    background-color: #1e3799; /* Deep blue background */
    padding: 0;
  }
  
  .custom-container {
    max-width: 800px;
    width: 100%;
    padding: 2rem;
  }
  
  .custom-card {
    width: 100%;
    background-color: #fff; /* White card background */
    border-radius: 12px;
    box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
    overflow: hidden;
    transition: transform 0.3s ease-in-out, box-shadow 0.3s ease-in-out;
  }
  
  .custom-card:hover {
    transform: translateY(-10px);
    box-shadow: 0 12px 24px rgba(0, 0, 0, 0.3);
  }
  
  .custom-card-section {
    padding: 30px;
    text-align: center;
  }
  
  .custom-card-title {
    font-size: 2.5rem;
    font-weight: 700;
    color: #1e3799; /* Deep blue text color */
    margin-bottom: 1rem;
  }
  
  .custom-card-description {
    font-size: 1.3rem;
    color: #333; /* Dark text color */
    margin-bottom: 1.5rem;
  }
  
  .custom-card-links {
    display: flex;
    justify-content: center;
  }
  
  .custom-card-link {
    margin: 0 10px;
    font-size: 1.2rem;
    color: #1e3799; /* Deep blue link color */
    text-decoration: none;
    border: 2px solid #1e3799; /* Deep blue border */
    padding: 0.5rem 1rem;
    border-radius: 10px;
    transition: background-color 0.3s ease-in-out, color 0.3s ease-in-out;
  }
  
  .custom-card-link:hover {
    background-color: #1e3799; /* Deep blue hover background */
    color: #fff; /* White hover text color */
  }
  </style>
  