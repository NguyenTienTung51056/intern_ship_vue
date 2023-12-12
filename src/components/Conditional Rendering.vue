<template>
    <div>
      <!-- v-if -->
      <h2>v-if Directive</h2>
      <h1 v-if="awesome">Vue is awesome!</h1>
  
      <!-- v-else -->
      <h2>v-else Directive</h2>
      <button @click="awesome = !awesome">Toggle</button>
      <h1 v-if="awesome">Vue is awesome!</h1>
      <h1 v-else>Oh no 😢</h1>
  
      <!-- v-else-if -->
      <h2>v-else-if Directive</h2>
      <div v-if="type === 'A'">A</div>
      <div v-else-if="type === 'B'">B</div>
      <div v-else-if="type === 'C'">C</div>
      <div v-else>Not A/B/C</div>
  
      <!-- v-if on <template> -->
      <h2>v-if on</h2>
      <template v-if="ok">
        <h1>Title</h1>
        <p>Paragraph 1</p>
        <p>Paragraph 2</p>
      </template>
  
      <!-- v-show -->
      <h2>v-show Directive</h2>
      <h1 v-show="ok">Hello!</h1>
  
      <!-- v-if vs. v-show -->
      <h2>v-if vs. v-show</h2>
      <div>
        <p>Toggle using v-if:</p>
        <button @click="toggleIf">Toggle</button>
        <h1 v-if="ifCondition">Rendered with v-if</h1>
      </div>
      <div>
        <p>Toggle using v-show:</p>
        <button @click="toggleShow">Toggle</button>
        <h1 v-show="showCondition">Rendered with v-show</h1>
      </div>
    </div>
      <!-- v-if with v-for (Note: Not recommended) -->
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  let awesome = ref(true);
  let type = ref('A');
  let ok = ref(true);
  let ifCondition = ref(true);
  let showCondition = ref(true);
  
  const toggleIf = () => {
    ifCondition.value = !ifCondition.value;
  };
  
  const toggleShow = () => {
    showCondition.value = !showCondition.value;
  };
  
  </script>
  
  <style scoped>
  /* Your styles go here */
  </style>
  