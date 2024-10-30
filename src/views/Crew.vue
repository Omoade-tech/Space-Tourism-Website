<template>
  <div class="container-fluid">
    <h1>02 MEET YOUR CREW</h1>

    <!-- Display crew member info if available -->
    <div class="row" v-if="filteredCrew">
      <!-- Content Column (right) -->
      <div class="content col-md-6 mb-4">
        <p>{{ filteredCrew.role }}</p>
        <h2>{{ filteredCrew.name }}</h2>
        <p>{{ filteredCrew.bio }}</p>

      </div>

      <!-- Image Column (left) -->
      <div class="col-md-6 d-flex align-items-center justify-content-center">
        <img :src="filteredCrew.images.png" alt="Crew Image" class="img-fluid" />
      </div>
    </div>
    <div v-else>
      <p>Loading crew data...</p>
    </div>

    <!-- Buttons Row -->
    <div class="btn-moon d-flex justify-content-start ">
      <button 
        @click="filterCrew('Douglas Hurley')" 
        class="btn me-2" 
        :class="{'active': activeCrew === 'Douglas Hurley'}"
      >
        
      </button>
      <button 
        @click="filterCrew('Mark Shuttleworth')" 
        class="btn me-2" 
        :class="{'active': activeCrew === 'Mark Shuttleworth'}"
      >
        
      </button>
      <button 
        @click="filterCrew('Victor Glover')" 
        class="btn me-2" 
        :class="{'active': activeCrew === 'Victor Glover'}"
      >
        
      </button>
      <button 
        @click="filterCrew('Anousheh Ansari')" 
        class="btn me-2" 
        :class="{'active': activeCrew === 'Anousheh Ansari'}"
      >
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      crew: [],             // All crew data
      filteredCrew: null,   // Currently selected crew member
      activeCrew: 'Douglas Hurley',  // Default to 'Douglas Hurley'
    };
  },
  mounted() {
    // Fetch crew data from the API
    fetch("http://localhost:3000/crew")
      .then((response) => response.json())
      .then((data) => {
        this.crew = data;
        // Automatically show 'Douglas Hurley' on load
        this.filterCrew('Douglas Hurley');
      })
      .catch((error) => console.log(error.message));
  },
  methods: {
    // Filter crew based on the selected name
    filterCrew(crewName) {
      this.filteredCrew = this.crew.find((crew) => crew.name === crewName);
      this.activeCrew = crewName;
    },
  },
};
</script>

<style scoped>
.container-fluid{

background-image: url('./src/assets/crew/background-crew-desktop.jpg');
background-size: cover;
  color: #ffffff;
  height: 130vh;
  margin: 0;
  width: 100%;
}
h1{
  padding-top: 90px;
  padding-left: 100px;
}
img{
  margin-top:-20px ;
}
.content{
  padding: 20px 100px;
  padding-top: 200px ;
}
button{
  background:white ;
  margin: 10px;
  height: 50px;
  width: 50px;
  border-radius: 50%;
}
.btn-moon{
  margin-top: -180px;
  margin-left: 90px;
}


</style>
