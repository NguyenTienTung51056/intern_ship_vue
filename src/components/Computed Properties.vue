<template>
    <div>
      <!-- Basic Example -->
      <h2>Basic Example</h2>
      <p>Has published books:</p>
      <span>{{ publishedBooksMessage }}</span>
  
      <!-- Computed Caching vs. Methods -->
      <h2>Computed Caching vs. Methods</h2>
      <p>Using computed property: {{ publishedBooksMessage }}</p>
      <p>Using method: {{ calculateBooksMessage() }}</p>
  
      <!-- Writable Computed -->
      <h2>Writable Computed</h2>
      <input v-model="fullName" placeholder="Enter full name" />
      <p>Full Name: {{ fullName }}</p>
    </div>
  </template>
  
  <script setup>
  import { ref, reactive, computed } from 'vue';
  
  // Basic Example
  const author = reactive({
    name: 'John Doe',
    books: ['Vue 2 - Advanced Guide', 'Vue 3 - Basic Guide', 'Vue 4 - The Mystery'],
  });
  
  const publishedBooksMessage = computed(() => (author.books.length > 0 ? 'Yes' : 'No'));
  
  // Computed Caching vs. Methods
  function calculateBooksMessage() {
    return author.books.length > 0 ? 'Yes' : 'No';
  }
  
  // Writable Computed
  const firstName = ref('John');
  const lastName = ref('Doe');
  const fullName = computed({
    get() {
      return firstName.value + ' ' + lastName.value;
    },
    set(newValue) {
      [firstName.value, lastName.value] = newValue.split(' ');
    },
  });
  </script>
  
  <style scoped>
  /* Your styles go here */
  </style>
  