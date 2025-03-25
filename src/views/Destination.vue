<template>
  <div class="container-fluid">
    <h1>01 Pick Your Destination</h1>

    <!-- Buttons Row -->
    <div class="btn-moon d-flex justify-content-end">
      <button 
        v-for="destination in destinations" 
        :key="destination.name" 
        @click="filterDestination(destination.name)" 
        class="btn" 
        :class="{'active': activeDestination === destination.name}"
      >
        {{ destination.name }}
      </button>
    </div>

    <!-- Content Row -->
    <div class="row">
      <!-- Image Column (left) -->
      <div class="col-md-6 d-flex align-items-center justify-content-center image">
        <img v-if="filteredDestination" :src="filteredDestination.images.png" alt="Destination Image" class="img-fluid" />
      </div>

      <!-- Content Column (right) -->
      <div class="content col-md-6">
        <div v-if="filteredDestination">
          <h2>{{ filteredDestination.name }}</h2>
          <p>{{ filteredDestination.description }}</p>
          <p><strong>Distance:</strong> {{ filteredDestination.distance }}</p>
          <span><strong>Travel Time:</strong> {{ filteredDestination.travel }}</span>
        </div>
        <div v-else>
          <p>Pick a destination to see more details.</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import data from '../../Data/data.json'

export default {
  data() {
    return {
      destinations: data.destinations,
      filteredDestination: data.destinations[0],
      activeDestination: 'Moon'
    }
  },
  methods: {
    filterDestination(destinationName) {
      const selectedDestination = this.destinations.find(
        destination => destination.name === destinationName
      )
      if (selectedDestination) {
        this.filteredDestination = selectedDestination
        this.activeDestination = destinationName
      }
    }
  }
}
</script>

<style scoped>
.container-fluid {
  background-image: url('@/assets/destination/background-destination-desktop.jpg');
  background-size: cover;
  color: #ffffff;
  height: 120vh;
  margin: 0;
  width: 100%;
}
button{
  color:#ffffff;
  margin: 7px;
  font-size: 24px;
}
.btn-moon{
  padding-top: 100px ;
  margin: 0 170px;
  
}
h1{
  padding-top: 90px;
  padding-left: 100px;
}

img{
  margin-top:-100px ;
}
.content{
  padding: 20px 100px;
}
@media screen and (min-width:320px) and (max-width:425px) {
  .container-fluid{
  height: 180vh;
  margin: 0;
  width: 100%;
}
.btn-moon{
  padding-top: 400px ;
  margin: 0px;
  padding-left:20px ;
  padding-right: 10px;
  
}
img{
  margin-top:-500px ;
}
button{
  color:#ffffff;
  font-size: 16px;
  margin: 0;
}
h1{
  padding-left: 0;
}
.content{
  padding:30px;
}
}
@media screen and (min-width: 426px) and (max-width: 768px) {
  .container-fluid{
  height: 180vh;
  margin: 0;
  width: 100%;
}
  .row {
    flex-direction: column; /* Stack the image first, followed by buttons and content */
  }

  img {
    margin-top: -700px;
    margin-left: 400px;
   
  }

  .btn-moon {
    display: flex;
    justify-content: center;
    padding: 20px 0;
    padding-top: 500px;
  }

  /* .content {
    display: flex; */
    /* margin: 1px 50px; */
    /* text-align: center;
    justify-content: center;
    
  } */

  button {
    margin: 5px;
    font-size: 18px;
  }

  h1 {
    text-align: center;
    padding-left: 0;
  }
}
</style>
