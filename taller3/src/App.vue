
<template>
  <div id="app" class="container">
    <button v-on:click="mangalista" class="boton-consultar">Consultar Manga al azar</button>
    <button v-on:click="animelista" class="boton-consultar">Consultar Anime al Azar</button>
    <button v-on:click="animesrecomendados" class="boton-consultar">Consultar Mangas Recomandados</button>
    <button v-on:click="getpoblacion" class="boton-consultar">Consultar Poblacion Paises</button>

    

    <div class="manga-list">
      <h1>Manga escogido:</h1>
      <Manga v-for="manga in mangas" v-bind:manga="manga" v-bind:key="manga.id"></Manga>
    </div>

    <div class="anime-list">
      <h1>Anime escogido:</h1>
      <Anime v-for="anime in animes" v-bind:anime="anime" v-bind:key="anime.id"></Anime>
    </div>

    <div class="recomendaciones-list">
      <h1>Animes Recomendados:</h1>
      <Recomendaciones v-for="recomendacion in recomendaciones" v-bind:recomendacion="recomendacion" v-bind:key="recomendacion.id"></Recomendaciones>
    </div>

    <div class="poblacion-list">
      <h1>Poblacion Paises:</h1>
      <Poblacion v-for="pais in paises" v-bind:pais="pais" v-bind:key="pais.country"></Poblacion>
    </div>



  </div>
</template>


<script>

import axios from 'axios';

import Manga from './components/Manga.vue';

import Anime from './components/Anime.vue';

import Recomendaciones from './components/Recomendaciones.vue';

import Poblacion from './components/Poblacion.vue';

export default{
  name: 'App',

  components: {
    Manga,

    Anime,

    Recomendaciones,

    Poblacion
  },

  data(){
    return{

      mangas: [],

      animes: [],

      recomendaciones: [],

      paises: []

    }



  },

  methods: {
  
    mangalista(){
      axios.get('https://api.jikan.moe/v4/random/manga')
      .then(response => {
        this.mangas = [response.data.data];
        console.log(response.data);
      })
      .catch(error => {
        console.log(error);
      });
    },

    
    animelista(){

    axios.get('https://api.jikan.moe/v4/random/anime')
      .then(response => {
        this.animes = [response.data.data];
        console.log(response.data);
      })
      .catch(error => {
        console.log(error);
      });
    },

    animesrecomendados(){

    axios.get('https://api.jikan.moe/v4/recommendations/anime')
      .then(response => {
        this.recomendaciones = response.data.data;
        console.log(response.data);
      })
      .catch(error => {
        console.log(error);
      });

  },

  getpoblacion(){
      
      axios.get('https://countriesnow.space/api/v0.1/countries/population')
        .then(response => {
          this.paises = response.data.data;
          console.log(this.paises);
        })
        .catch(error => {
          console.log(error);
        });
  }

  }
  


}

</script>
<style scoped>

.container {
  display: flex;
  height: 100vh;
  width: 100vw;
  background-color: darkcyan;
  padding-top: 20px; 
}


.title {
  margin-top: 4vh;
  font-size: 2rem;
  text-align: center;
  margin-bottom: 20px; 
}

.boton-consultar {
  padding: 10px 20px;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  margin-bottom: 20px;
  height: 5vh;
  width: 10vw;
  margin-top: 4vh;
}

.character-list {
  text-align: center;
}
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

.card-header {
  border-radius: 5px 5px 0 0;
  padding: 10px;
}

.card-content {
  padding: 10px;
}
</style>