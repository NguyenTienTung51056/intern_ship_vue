<!-- ChildrenClassBinding.vue -->
<template>
    <div>
      <!-- Your component content -->
      <p class="inside component child">inside component child</p>
      <span v-html="classes.template"></span>
    </div>
  </template>
  
  <script setup>
  defineProps(['classes']);
  </script>
  