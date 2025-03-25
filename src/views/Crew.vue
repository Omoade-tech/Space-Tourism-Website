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
        v-for="member in crew" 
        :key="member.name" 
        @click="filterCrew(member.name)" 
        class="btn me-2" 
        :class="{'active': activeCrew === member.name}"
      >
        
      </button>
    </div>
  </div>
</template>

<script>
import data from '../../Data/data.json'

export default {
  data() {
    return {
      crew: data.crew,
      filteredCrew: data.crew[0],
      activeCrew: 'Douglas Hurley'
    }
  },
  methods: {
    filterCrew(crewName) {
      const selectedCrew = this.crew.find(crew => crew.name === crewName)
      if (selectedCrew) {
        this.filteredCrew = selectedCrew
        this.activeCrew = crewName
      }
    }
  }
}
</script>

<style scoped>
.container-fluid {
  background-image: url('@/assets/crew/background-crew-desktop.jpg');
  background-size: cover;
  color: #ffffff;
  height: 100vh;
  margin: 0;
  width: 100%;
  padding: 2rem;
}

h1 {
  padding-top: 2rem;
  font-size: 2.5rem;
}

.row {
  margin-bottom: 2rem;
}

.content {
  padding: 2rem;
}

.image {
  padding: 2rem;
}

.btn-moon {
  position: fixed;
  bottom: 2rem;
  left: 50%;
  transform: translateX(-50%);
  gap: 1rem;
  flex-wrap: wrap;
  justify-content: center;
}

button {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  background-color: rgba(255, 255, 255, 0.1);
  color: #ffffff;
  border: 1px solid rgba(255, 255, 255, 0.5);
  font-weight: bold;
  cursor: pointer;
  transition: all 0.3s ease;
  font-size: 0.8rem;
  padding: 1rem;
  margin: 0.5rem;
}

button:hover {
  background-color: rgba(255, 255, 255, 0.2);
}

button.active {
  background-color: #ffffff;
  color: #0b0d17;
}

@media screen and (max-width: 768px) {
  .container-fluid {
    height: auto;
    min-height: 100vh;
    padding: 1rem;
  }

  h1 {
    padding-top: 1rem;
    font-size: 2rem;
    text-align: center;
  }

  .row {
    flex-direction: column;
    align-items: center;
    text-align: center;
  }

  .content {
    padding: 1rem;
    width: 100%;
    max-width: 400px;
    text-align: center;
  }

  .image {
    padding: 1rem;
    width: 100%;
    max-width: 400px;
  }

  .btn-moon {
    position: static;
    margin-top: 2rem;
    flex-direction: row;
    justify-content: center;
    gap: 1rem;
    flex-wrap: wrap;
  }

  button {
    width: 80px;
    height: 80px;
    font-size: 0.7rem;
    margin: 0.5rem;
  }

  img {
    width: 100%;
    max-width: 300px;
    height: auto;
  }
}

@media screen and (max-width: 480px) {
  h1 {
    font-size: 1.5rem;
    padding-top: 0.5rem;
  }

  .btn-moon {
    flex-wrap: wrap;
    justify-content: center;
  }

  button {
    width: 70px;
    height: 70px;
    font-size: 0.6rem;
    margin: 0.25rem;
  }

  .content {
    padding: 0.5rem;
  }

  .image {
    padding: 0.5rem;
  }

  img {
    max-width: 250px;
  }
}
</style>
