<script setup>
  import TemplateSyntax from './components/Template Syntax.vue';
  import Reactivity_Fundamentals from './components/Reactivity Fundamentals.vue';
  import { ref } from 'vue';

 const templateSyntax = ref(false);
 const reactivityFundamentals = ref(false);

 const displayTemplateSyntax = () => {
  templateSyntax.value = !templateSyntax.value;
};

const displayReactivityFundamentals = () => {
  reactivityFundamentals.value = !reactivityFundamentals.value;
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
    <button @click="displayTemplateSyntax" >TemplateSyntax</button>
    <button @click="displayReactivityFundamentals" >Reactivity_Fundamentals</button>
    <TemplateSyntax v-if="templateSyntax"/>
    <Reactivity_Fundamentals v-if="reactivityFundamentals"/>
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
