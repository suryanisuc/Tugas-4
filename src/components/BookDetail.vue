<template>
    <div class="card mt-4">
      <div class="card-body">
        <h2 class="card-title">{{ book.title }}</h2>
        <h4 class="card-subtitle mb-2 text-muted">{{ book.author }}</h4>
        <p class="card-text">{{ book.description }}</p>
      </div>
    </div>
  </template>
  
  <script setup>
  import { defineProps } from 'vue';
  
  const props = defineProps({
    book: Object
  });
  </script>
  
  <style scoped>
  /* Tambahan styling khusus untuk BookDetail */
  .card {
    border: 1px solid #007bff;
  }
  .card-title {
    font-size: 1.5rem;
    color: #007bff;
  }
  .card-subtitle {
    font-size: 1.25rem;
  }
  </style>
  