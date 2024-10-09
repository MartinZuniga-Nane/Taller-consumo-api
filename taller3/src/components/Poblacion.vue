<template>
    <div class="columna">
      <div class="card">
        <div class="card-header"></div>
        <div class="card-content">
            <h2>Nombre</h2>
          <h3>{{ pais.country }}</h3>
          <h2>Año</h2>
          <h3>{{ pais.populationCounts[0]?.year }}</h3>
          <h2>Poblacion ese año</h2>
          <h3>{{ pais.populationCounts[0]?.value }}</h3>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: ['pais']
  }
  </script>
  
  <style scoped>
  .card {
    background-color: white;
    border-radius: 5px;
    margin-top: 20px;
    padding: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    color: black;
    height: 50vh;
    width: 18vw;
  }
  
  .card-content {
    padding: 10px;
  }
  </style>
  