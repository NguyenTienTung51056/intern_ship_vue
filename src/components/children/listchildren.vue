<script setup>
defineProps(['item'])
</script>



<template>
    <li>
      {{ item.message }}
      <!-- <button @click="$emit('remove')">Remove</button> -->
    </li>
  </template>