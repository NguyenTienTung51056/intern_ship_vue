<script setup>
  import TemplateSyntax from './components/Template Syntax.vue';
  import Reactivity_Fundamentals from './components/Reactivity Fundamentals.vue';
  import { ref } from 'vue';
  import ComputedProperties from './components/Computed Properties.vue';
  import classAndStyleBindings from './components/Class and Style Bindings.vue';
  import ConditionalRendering from './components/Conditional Rendering.vue';
  import ListRendering from './components/List_rendering.vue';
  import EventHandling from './components/EventHandling.vue'

 const templateSyntax = ref(false);
 const reactivityFundamentals = ref(false)  
 const computedProperties = ref(false);
 const classAndStyleBindin = ref(false);
 const conditionalRenderin = ref(false);
 const listRenderin = ref(false);
 const eventHandling = ref(false);

 const displayEventHandling = () => {
  eventHandling.value = !eventHandling.value;
 }

 const displayListRendering = () => {
  listRenderin.value = !listRenderin.value;
 }

 const displayConditionalRendering = () => {
  conditionalRenderin.value = !conditionalRenderin.value;
 }
 const displayTemplateSyntax = () => {
  templateSyntax.value = !templateSyntax.value;
};

const displayReactivityFundamentals = () => {
  reactivityFundamentals.value = !reactivityFundamentals.value;
};

const displayComputedProperties = () => {
  computedProperties.value = !computedProperties.value;
};

const displayClassAndStyleBindings = () => {
  classAndStyleBindin.value = !classAndStyleBindin.value;
};


</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <!-- <HelloWorld msg="You did it!" /> -->
    </div>
  </header>

  <main>
    <div class="card d-flex justify-content-center align-items-center  shadow p-3 mb-5 bg-body rounded rounded border-0">
      <div class="mb-3">
        <button class="btn btn-outline-primary" type="button" @click="displayTemplateSyntax" >Template Syntax</button>
      </div>

      <div class="mb-3">
        <button type="button" class="btn btn-outline-primary" @click="displayReactivityFundamentals" >Reactivity Fundamentals</button>
      </div>
      <div class="mb-3">
        <button type="button" class="btn btn-outline-primary" @click="displayComputedProperties">Computed Properties</button>
      </div>
      <div class="mb-3">
        <button type="button" class="btn btn-outline-primary" @click="displayClassAndStyleBindings">Class and Style Bindings</button>
      </div>
      <div class="mb-3">
        <button type="button" class="btn btn-outline-primary" @click="displayConditionalRendering">Conditional Rendering </button>
      </div>
      <div class="mb-3">
        <button type="button" class="btn btn-outline-primary" @click="displayListRendering">List renderring</button>
      </div>
      <div class="mb-3">
        <button type="button" class="btn btn-outline-primary" @click="displayEventHandling">Event Handling</button>
      </div>
    </div>
    <TemplateSyntax v-if="templateSyntax"/>
    <classAndStyleBindings v-if="classAndStyleBindin" />
    <ComputedProperties v-if="computedProperties" />
    <Reactivity_Fundamentals v-if="reactivityFundamentals"/>
    <ConditionalRendering v-if="conditionalRenderin"/>
    <ListRendering v-if="listRenderin" />
    <EventHandling v-if="eventHandling"/>
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
