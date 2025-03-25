<template>
  <div class="container-fluid">
    <h1>03 SPACE LAUNCH 101</h1>

    <div
      class="row align-items-center mb-4"
      v-for="tech in filteredTechnology"
      :key="tech.name"
    >
      <!-- Content (Left) -->
      <div class="content col-md-6">
        <h2>{{ tech.name }}</h2>
        <p>{{ tech.description }}</p>
      </div>

      <!-- Image (Right) -->
      <div class="image col-md-6 d-flex justify-content-end">
        <img 
          :src="tech.images.portrait" 
          alt="technology-image" 
          class="img-fluid"
        />
      </div>
    </div>

    <!-- Buttons Row -->
    <div class="btn-tech d-flex mb-4">
      <button 
        v-for="(tech, index) in technology" 
        :key="tech.name" 
        @click="filterTechnology(tech.name)" 
        class="btn me-2" 
        :class="{'active': activeTechnology === tech.name}"
      >
        {{ index + 1 }}
      </button>
    </div>
  </div>
</template>

<script>
import data from '../../Data/data.json'

export default {
  data() {
    return {
      technology: data.technology,
      filteredTechnology: [data.technology[0]],
      activeTechnology: 'Launch vehicle'
    }
  },
  methods: {
    filterTechnology(type) {
      const selectedTechnology = this.technology.find(
        tech => tech.name === type
      )
      if (selectedTechnology) {
        this.filteredTechnology = [selectedTechnology]
        this.activeTechnology = type
      }
    }
  }
}
</script>

<style scoped>
.container-fluid {
  background-image: url('@/assets/technology/background-technology-desktop.jpg');
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

.btn-tech {
  position: fixed;
  bottom: 2rem;
  left: 50%;
  transform: translateX(-50%);
  gap: 1rem;
  flex-direction: column;
  align-items: center;
}

button {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  background-color: rgba(255, 255, 255, 0.1);
  color: #ffffff;
  border: 1px solid rgba(255, 255, 255, 0.5);
  font-weight: bold;
  cursor: pointer;
  transition: all 0.3s ease;
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
  }

  .image {
    padding: 1rem;
    width: 100%;
    max-width: 400px;
  }

  .btn-tech {
    position: static;
    margin-top: 2rem;
    flex-direction: row;
    justify-content: center;
    gap: 1rem;
  }

  button {
    width: 40px;
    height: 40px;
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

  .btn-tech {
    flex-wrap: wrap;
    justify-content: center;
  }

  button {
    width: 35px;
    height: 35px;
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
