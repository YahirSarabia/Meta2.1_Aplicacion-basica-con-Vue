<script setup>
import TablaPelis from '../components/TablaPelicula.vue'
</script>

<template>
    <div class="pelicula">
      <TablaPelis />
    </div>
  </template>
  
  <style>
  @media (min-width: 1024px) {
    .pelicula {
      min-height: 100vh;
      display: flex;
      align-items: center;
    }
  }
  </style>
  