<template>
  <div class="container-fluid" v-if="filteredTechnology.length > 0">
    <h1>03 SPACE LAUNCH 101</h1>

    <div
      class="row align-items-center mb-4"
      v-for="x in filteredTechnology"
      :key="x.id"
    >
      <!-- Content (Left) -->
      <div class="content col-md-6">
        <h2>{{ x.name }}</h2>
        <p>{{ x.description }}</p>
      </div>

      <!-- Image (Right) -->
      <div class="image col-md-6 d-flex justify-content-end">
        <img 
          :src="x.images.portrait" 
          alt="technology-image" 
          class="img-fluid"
        />
      </div>
    </div>
  </div>
  <div v-else>
    <p>Loading all technology...</p>
  </div>

  <!-- Buttons Row -->
  <div class="btn-tech d-flex mb-4">
    <button 
      @click="filterTechnology('Launch vehicle')" 
      class="btn me-2" 
      :class="{'active': activeTechnology === 'Launch vehicle'}"
    >
      1
    </button>
    <button 
      @click="filterTechnology('Spaceport')" 
      class="btn me-2" 
      :class="{'active': activeTechnology === 'Spaceport'}"
    >
      2
    </button>
    <button 
      @click="filterTechnology('Space capsule')" 
      class="btn me-2" 
      :class="{'active': activeTechnology === 'Space capsule'}"
    >
      3
    </button>
  </div>

</template>

<script>
export default {
  data() {
    return {
      technology: [],
      filteredTechnology: [],
      activeTechnology: 'Launch vehicle'
    };
  },
  mounted() {
    fetch("http://localhost:3000/technology")
      .then((response) => response.json())
      .then((data) => {
        this.technology = data;
        this.filterTechnology(this.activeTechnology); // Initial filter
      })
      .catch((error) => console.log(error.message));
  },
  methods: {
    filterTechnology(type) {
      this.activeTechnology = type;
      this.filteredTechnology = this.technology.filter(
        (tech) => tech.name === type
      );
    }
  }
};
</script>

<style scoped>
/* Add any custom styles here */
.container-fluid{

background-image: url('./src/assets/crew/background-crew-desktop.jpg');
background-size: cover;
  color: #ffffff;
  height: 125vh;
  margin: 0;
  width: 100%;
}
h1{
  padding-top: 90px;
  padding-left: 100px;
}
.content{
  padding-left: 200px;
  
}
.btn-tech{
  flex-direction:column;
  width: 5%;
  margin-top: -450px;
  margin-left: 6rem;
  color:#ffffff;
}
button {
  color:black;
  background-color: #ffffff;
  margin-left: 20px;
  margin-bottom: 1.5rem;
  height: 40%;
  border-radius: 50%;
}
img{
  margin-right: 40px;
  padding-bottom:50px;
}
</style>
