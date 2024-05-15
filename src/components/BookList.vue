<template>
    <div>
      <slot name="header"></slot>
      <ul class="list-group">
        <BookItem
          v-for="book in books"
          :key="book.id"
          :book="book"
          @click.native="selectBook(book)"
          class="list-group-item list-group-item-action"
        ></BookItem>
      </ul>
    </div>
  </template>
  
  <script setup>
  import { defineProps, defineEmits } from 'vue';
  import BookItem from './BookItem.vue';
  
  const props = defineProps({
    books: Array
  });
  
  const emit = defineEmits(['book-selected']);
  
  function selectBook(book) {
    emit('book-selected', book);
  }
  </script>
  
  <style scoped>
  .list-group-item {
    cursor: pointer;
    width: 50%;
  }
  </style>
  