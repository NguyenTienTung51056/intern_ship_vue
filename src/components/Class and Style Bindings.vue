<template>
    <div>
      <!-- Binding to Objects -->
      <h2>Binding to Objects</h2>
      <div :class="{ active: isActive, 'text-danger': hasError }">Toggle Classes</div>
  
      <!-- Binding to Arrays -->
      <h2>Binding to Arrays</h2>
      <div :class="[activeClass, errorClass]">Multiple Classes</div>
      <div :class="[isActive ? activeClass : '', errorClass]">Conditional Classes</div>
      <div :class="[{ active: isActive }, errorClass]">Object Syntax in Array</div>
  
      <!-- With Components -->
      <h2>With Components</h2>
      <MyComponent :class="{ active: isActive }" />
  
      <!-- Binding Inline Styles -->
      <h2>Binding Inline Styles</h2>
      <div :style="{ color: activeColor, fontSize: fontSize + 'px' }">Inline Styles</div>
      <div :style="{ 'font-size': fontSize + 'px' }">Kebab-cased CSS Property</div>
      <div :style="styleObject">Object Style Binding</div>
  
      <!-- Binding to Arrays -->
      <div :style="[baseStyles, overridingStyles]">Multiple Style Objects</div>
    </div>
  </template>
  
  <script setup>
  import { ref, reactive, computed } from 'vue';
  
  // Binding to Objects
  const isActive = ref(true);
  const hasError = ref(false);
  
  // Binding to Arrays
  const activeClass = ref('active');
  const errorClass = ref('text-danger');
  
  const baseStyles = reactive({
    color: 'blue',
    fontSize: '20px',
  });
  
  const overridingStyles = reactive({
    color: 'red',
    fontWeight: 'bold',
  });
  
  // With Components
  const MyComponent = {
    template: '<p :class="$attrs.class">Hi!</p><span>This is a child component</span>',
  };
  
  // Binding Inline Styles
  const activeColor = ref('red');
  const fontSize = ref(30);
  
  const styleObject = reactive({
    color: 'red',
    fontSize: '13px',
  });
  </script>
  
  <style scoped>
  /* Your styles go here */
  </style>
  