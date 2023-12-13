<template>
    <div>
      <!-- Using a ref on a DOM element -->
      <input ref="input" />
  
      <!-- Using a ref inside v-for -->
      <ul>
        <li v-for="item in list" :key="item.id" :ref="el => handleItemRef(el, item.id)">
          {{ item.message }}
        </li>
      </ul>
  
      <!-- Using a function ref on a DOM element -->
      <input :ref="el => handleInputRef(el)" />
  
      <!-- Using a ref on a child component -->
      <div>
        <Child ref="childRef" />
        <button @click="focusChildInput">Focus Child Input</button>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref, onMounted, watchEffect, defineExpose } from 'vue';
  import Child from './children/Child.vue';
  
  const input = ref(null);
  const list = ref([
    { id: 1, message: 'Hello' },
    { id: 2, message: 'World' },
  ]);
  const itemRefs = ref({});
  
  onMounted(() => {
    // Accessing the ref after component is mounted
    if (input.value) {
      input.value.focus();
    }
  
    // Watching changes of a template ref
    watchEffect(() => {
      if (input.value) {
        input.value.focus();
      } else {
        // Not mounted yet, or the element was unmounted (e.g., by v-if)
      }
    });
  
    // Accessing the ref array inside v-for
    console.log(itemRefs.value);
  });
  
  const childRef = ref(null);
  
  // method to focus the child input
  const focusChildInput = () => {
    if (childRef.value) {
      // Accessing the input element in the child component using the ref
      childRef.value.$refs.childInput.focus();
    }
  };
  
  // Handling refs inside v-for
  const handleItemRef = (el, id) => {
    itemRefs.value[id] = el;
  };
  
  // Handling function ref on a DOM element
  const handleInputRef = (el) => {
    input.value = el;
  };
  
  // Child component using <script setup>
  defineExpose({
    childRef,
  });
  
  // If Child component is using Options API or not using <script setup>
  // Uncomment the following lines
  // const childInstance = ref(null);
  // onMounted(() => {
  //   childInstance.value = child.value.$refs.child;
  // });
  </script>
  