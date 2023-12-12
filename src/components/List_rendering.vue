<template>
  <div>
    <!-- v-for -->
    <h2>v-for Directive</h2>
    <ul>
      <li v-for="item in items" :key="item.id">
        {{ item.message }}
      </li>
    </ul>

    <!-- v-for with index -->
    <h2>v-for with Index</h2>
    <ul>
      <li v-for="(item, index) in items" :key="item.id">
        {{ parentMessage }} - {{ index }} - {{ item.message }}
      </li>
    </ul>

    <!-- v-for with destructuring -->
    <h2>v-for with Destructuring</h2>
    <ul>
      <li v-for="{ message } in items" :key="message">
        {{ message }}
      </li>
    </ul>

    <!-- Nested v-for -->
    <h2>Nested v-for</h2>
    <ul>
      <li v-for="item in items" :key="item.id">
        <span v-for="childItem in item.children" :key="childItem.id">
          {{ item.message }} {{ childItem }}
        </span>
      </li>
    </ul>

    <!-- v-for with Object -->
    <h2>v-for with Object</h2>
    <ul>
      <li v-for="(value, key) in myObject" :key="key">
        {{ key }}: {{ value }}
      </li>
    </ul>

    <!-- v-for with Range -->
    <h2>v-for with Range</h2>
    <span v-for="n in 10" :key="n">{{ n }}</span>

    <!-- v-for on <template> -->
    <h2>v-for on</h2>
    <ul>
      <template v-for="item in items" :key="item.id">
        <li>{{ item.message }}</li>
        <li class="divider" role="presentation"></li>
      </template>
    </ul>

    <!-- v-for with v-if -->
    <h2>v-for with v-if</h2>
    <ul>
      <li v-for="todo in todos" :key="todo.name" v-if="!todos.isComplete">
        {{ todo.name }}
      </li>
    </ul>

    <!-- v-for with key -->
    <h2>v-for with key</h2>
    <ul>
      <li v-for="item in items" :key="item.id">
        {{ item.message }}
      </li>
    </ul>

    <!-- v-for with Component -->
    <h2>v-for with Component</h2>
    <MyComponent
      v-for="(item, index) in items"
      :item="item"
      :index="index"
      :key="item.id"
    />

    <!-- Array Change Detection -->
    <h2>Array Change Detection</h2>
    <button @click="addItem">Add Item</button>
    <button @click="removeItem">Remove Item</button>
    <ul>
      <li v-for="item in items" :key="item.id">{{ item.message }}</li>
    </ul>
  </div>
</template>

<script setup>
import { ref, reactive, computed } from 'vue';

let parentMessage = 'Parent';
let items = ref([
  { id: 1, message: 'Foo', children: [1, 2, 3] },
  { id: 2, message: 'Bar', children: [4, 5, 6] }
]);
let myObject = reactive({
  title: 'How to do lists in Vue',
  author: 'Jane Doe',
  publishedAt: '2016-04-10'
});
let todos = ref([
  { name: 'Task 1', isComplete: false },
  { name: 'Task 2', isComplete: true },
  { name: 'Task 3', isComplete: false }
]);
let evenNumbers = computed(() => items.value.filter((n) => n % 2 === 0));

const sets = ref([
  [1, 2, 3, 4, 5],
  [6, 7, 8, 9, 10]
]);

function even(numbers) {
  return numbers.filter((number) => number % 2 === 0);
}

const addItem = () => {
  items.value.push({ id: items.value.length + 1, message: 'New Item', children: [] });
};

const removeItem = () => {
  items.value.pop();
};
</script>

<style scoped>
/* Your styles go here */
</style>
