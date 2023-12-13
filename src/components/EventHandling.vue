<template>
    <div>
      <!-- Listening to Events -->
      <h2>Listening to Events</h2>
      <!-- Inline Handlers -->
      <h3>Inline Handlers</h3>
      <button type="button" class="btn btn-secondary" @click="count++">Add 1</button>
      <p>Count is: {{ count }}</p>
  
      <!-- Method Handlers -->
      <h3>Method Handlers</h3>
      <button type="button" class="btn btn-secondary" @click="greet">Greet</button>
  
      <!-- Calling Methods in Inline Handlers -->
      <h3>Calling Methods in Inline Handlers</h3>
      <button type="button" class="btn btn-secondary" @click="say('hello')">Say hello</button>
      <button type="button" class="btn btn-secondary" @click="say('bye')">Say bye</button>
  
      <!-- Accessing Event Argument in Inline Handlers -->
      <h3>Accessing Event Argument in Inline Handlers</h3>
      <button type="button" class="btn btn-secondary" @click="warn('Form cannot be submitted yet.', $event)">Submit</button>
      <button type="button" class="btn btn-secondary" @click="(event) => warn('Form cannot be submitted yet.', event)">Submit</button>
  
      <!-- Event Modifiers -->
      <h2>Event Modifiers</h2>
      <!-- .stop, .prevent, .self Modifiers -->
      <h3>.stop, .prevent, .self Modifiers</h3>
      <a @click.stop="doThis">Stop Propagation</a>
      <form @submit.prevent="onSubmit">Prevent Submit</form>
      <a @click.stop.prevent="doThat">Stop and Prevent</a>
      <div @click.self="doThat">Only Self</div>
  
      <!-- .capture, .once, .passive Modifiers -->
      <h3>.capture, .once, .passive Modifiers</h3>
      <div @click.capture="doThis">Capture Mode</div>
      <a @click.once="doThis">Once</a>
      <div @scroll.passive="onScroll">Passive Scroll</div>
  
      <!-- Key Modifiers -->
      <h2>Key Modifiers</h2>
      <input @keyup.enter="submit" />
      <input @keyup.page-down="onPageDown" />
  
      <!-- Key Aliases -->
      <h3>Key Aliases</h3>
      <input @keyup.enter="submit" />
      
      <!-- System Modifier Keys -->
      <h3>System Modifier Keys</h3>
      <input @keyup.ctrl="doSomething" />
      <input @keyup.alt.enter="clear" />
  
      <!-- .exact Modifier -->
      <h3>.exact Modifier</h3>
      <button type="button" class="btn btn-secondary" @click.ctrl="onClick">Ctrl + Click</button>
      <button type="button" class="btn btn-secondary" @click.ctrl.exact="onCtrlClick">Only Ctrl Click</button>
      <button type="button" class="btn btn-secondary" @click.exact="onClick">No Modifiers</button>
  
      <!-- Mouse Button Modifiers -->
      <h2>Mouse Button Modifiers</h2>
      <button type="button" class="btn btn-secondary" @mousedown.left="onLeftClick">Left Click</button>
      <button type="button" class="btn btn-secondary" @mousedown.right="onRightClick">Right Click</button>
      <button type="button" class="btn btn-secondary" @mousedown.middle="onMiddleClick">Middle Click</button>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  let count = ref(0);
  let name = ref('Vue.js');
  
  function greet(event) {
    alert(`Hello ${name.value}!`);
    if (event) {
      alert(event.target.tagName);
    }
  }
  
  function say(message) {
    alert(message);
  }
  
  function warn(message, event) {
    if (event) {
      event.preventDefault();
    }
    alert(message);
  }
  
  function doThis() {
    alert('Doing This');
  }
  
  function doThat() {
    alert('Doing That');
  }
  
  function onSubmit() {
    alert('Form Submitted');
  }
  
  function onPageDown() {
    alert('Page Down Pressed');
  }
  
  function onScroll() {
    alert('Scrolling');
  }
  
  function submit() {
    alert('Enter Pressed');
  }
  
  function doSomething() {
    alert('Ctrl Pressed');
  }
  
  function clear() {
    alert('Alt + Enter Pressed');
  }
  
  function onClick() {
    alert('Click Event');
  }
  
  function onCtrlClick() {
    alert('Ctrl + Click Event');
  }
  
  function onLeftClick() {
    alert('Left Click');
  }
  
  function onRightClick() {
    alert('Right Click');
  }
  
  function onMiddleClick() {
    alert('Middle Click');
  }
  </script>
  
  <style scoped>
  /* Your styles go here */
  </style>
  