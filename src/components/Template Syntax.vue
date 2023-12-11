  <script setup>
  const dynamicId = 'my-dynamic-id';
  const dynamicIdShorthand = 'my-dynamic-id-shorthand';
  const isButtonDisabled = false;
  const objectOfAttrs = {
    id: 'container',
    class: 'wrapper',
    style: 'color: red;',
  };
  const number = 42;
  const ok = true;
  const message = 'Hello, Vue!';
  const id = 'example';
  const date = new Date();
  const url = 'https://example.com';
  const attributeName = 'href';
  const eventName = 'click';
  
  const seen = true;
  
  const toTitleDate = (date) => date.toISOString();
  const formatDate = (date) => date.toDateString();

    const doSomething = () => {
        alert('https://example.com');
    };
  
  const onSubmit = () => {
    console.log('Form submitted!');
  };
  </script>

<template>
    <div>
      <!-- Attribute Bindings -->
      <h2>Attribute Bindings</h2>
      <div :id="dynamicId"></div>
      <hr>
  
      <!-- Shorthand -->
      <h2>Shorthand</h2>
      <div :id="dynamicIdShorthand"></div>
      <hr>
      <!-- Boolean Attributes -->
      <h2>Boolean Attributes</h2>
      <button :disabled="isButtonDisabled">Button</button>
        <hr>
      <!-- Dynamically Binding Multiple Attributes -->
      <h2>Dynamically Binding Multiple Attributes</h2>
      <div v-bind="objectOfAttrs">This div has dynamic attributes</div>
      <hr>
      <!-- Using JavaScript Expressions -->
      <h2>Using JavaScript Expressions</h2>
      <div :id="`list-${id}`"></div>
      <p>{{ number + 1 }}</p>
      <p>{{ ok ? 'YES' : 'NO' }}</p>
      <p>{{ message.split('').reverse().join('') }}</p>
      <hr>
      <!-- Calling Functions -->
      <h2>Calling Functions</h2>
      <time :title="toTitleDate(date)" :datetime="date">
        {{ formatDate(date) }}
      </time>
      <hr>
      <!-- Restricted Globals Access -->
      <h2>Restricted Globals Access</h2>
      <p>{{ Math.random() }}</p>
      <hr>
      <!-- Directives -->
      <h2>Directives</h2>
      <p v-if="seen">Now you see me</p>
      <hr>
      <!-- Arguments -->
      <h2>Arguments</h2>
      <a :href="url">Link</a>
      <a class="thea" @click="doSomething">Click me</a>
      <hr>
      <!-- Dynamic Arguments -->
      <h2>Dynamic Arguments</h2>
      <a :[attributeName]="url">Link</a>
      <a @[eventName]="doSomething">Click me</a>
      <hr>
      <!-- Modifiers -->
      <h2>Modifiers</h2>
      <form @submit.prevent="onSubmit">
        Submit Form (Submit event is prevented)
        <button type="submit">test</button>
      </form>
    </div>
  </template>



<style>


a{
    cursor: pointer;
}



</style>
  