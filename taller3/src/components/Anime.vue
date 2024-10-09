<script >

export default{
    props: ['anime']
}

</script>

<template>

    <div class="columna">
      <div class="card">
        <div class="card-header"><img v-bind:src="anime.images.jpg.image_url" alt=/></div>
        <div class="card-content">
            <h3>{{ anime.title }}</h3>
        </div>
        </div>
    </div>
 
</template>

<style scoped>

.manga-list {
  text-align: center;
  width: 100%;
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
