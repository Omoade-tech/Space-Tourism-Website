<script setup>
import NavBar from "./components/NavBar.vue";

import { RouterLink, RouterView } from "vue-router";
</script>

<template>
  <div id="app">
    <NavBar></NavBar>
    <!-- <Destination></Destination> -->
  </div>
</template>

<style scoped>
.nav-item {
  color: red;
  background: green;
}
</style>
