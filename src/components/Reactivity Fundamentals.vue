<template>
    <div>
      <h2>Reactivity Fundamentals</h2>
  
      <!-- Declaring Reactive State with ref() -->
      <h2>Declaring Reactive State with ref()</h2>
      <div>{{ count }}</div>
      <button @click="increment">Increment</button>
  
      <!-- Ref Unwrapping in Templates -->
      <h2>Ref Unwrapping in Templates</h2>
      <div>
        <!-- This works as expected -->
        {{ count + 1 }}
      </div>
      <div>
        <!-- This does NOT work as expected -->
        {{ object.id + 1 }}
      </div>
      <div>
        <!-- Ref unwrapping in text interpolation -->
        {{ object.id }}
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref, reactive } from 'vue';
  
  // Declaring Reactive State with ref()
  const count = ref(0);
  
  function increment() {
    count.value++;
  }
  
  // Using script setup
  const object = reactive({
    id: ref(1),
  });
  </script>
  