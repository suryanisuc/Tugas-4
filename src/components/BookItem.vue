<template>
    <li>
      <div class="d-flex align-items-center">
        <img :src="book.cover" alt="Sampul Buku" class="img-thumbnail mr-3" style="width: 60px; height: 60px;">
        <div>
          <h3>{{ book.title }}</h3>
          <p>{{ book.author }}</p>
        </div>
      </div>
    </li>
  </template>
  
  <script setup>
  import { defineProps } from 'vue';
  
  const props = defineProps({
    book: Object
  });
  </script>
  
  <style scoped>
  li {
    margin-bottom: 10px;
  }
  h3 {
    margin: 0;
    font-size: 1.25rem;
  }
  p {
    margin: 0;
    color: gray;
  }
  </style>
  