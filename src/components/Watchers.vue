<script setup>
import { ref, watch, watchEffect, reactive } from 'vue'

const question = ref('')
const answer = ref('Questions usually contain a question mark. ;-)')
const loading = ref(false)

// watch works directly on a ref
watch(question, async (newQuestion, oldQuestion) => {
    if (newQuestion.includes('?')) {
        loading.value = true
        answer.value = 'Thinking...'
        try {
            const res = await fetch('https://yesno.wtf/api')
            answer.value = (await res.json()).answer
        } catch (error) {
            answer.value = 'Error! Could not reach the API. ' + error
        } finally {
            loading.value = false
        }
    }
})

// Watch Source Types
const x = ref(0);
const y = ref(0);

watch(x, (newX) => {
    console.log(`x is ${newX}`);
});

watch(() => x.value + y.value, (sum) => {
    console.log(`sum of x + y is: ${sum}`);
});

watch([x, () => y.value], ([newX, newY]) => {
    console.log(`x is ${newX} and y is ${newY}`);
});

// Deep Watchers
const obj = reactive({ count: 0 });

watch(obj, (newValue, oldValue) => {
    console.log('Deep watcher fired:', newValue, oldValue);
});

function incrementCount() {
    obj.count++;
}

// Eager Watchers
const source = ref(10);
const eagerValue = ref(0);

watch(source, (newValue, oldValue) => {
    console.log(`Source changed from ${oldValue} to ${newValue}`);
    eagerValue.value = newValue * 2;
}, { immediate: true });

function changeEagerValue() {
    source.value = Math.floor(Math.random() * 100);
}

// watchEffect()
const todoId = ref(1);
const data = ref(null);

watchEffect(async () => {
    const response = await fetch(`https://jsonplaceholder.typicode.com/todos/${todoId.value}`);
    data.value = await response.json();
});

function changeTodoId() {
    todoId.value = Math.floor(Math.random() * 10) + 1;
}
</script>

<template>
    <p>
        Ask a yes/no question:
        <input v-model="question" :disabled="loading" />
    </p>
    <p>{{ answer }}</p>


    <!-- Watch Source Types -->
    <div>
        <h3>Watch Source Types</h3>
        <p>x: {{ x }}, y: {{ y }}</p>
    </div>

    <!-- Deep Watchers -->
    <div>
        <h3>Deep Watchers</h3>
        <p>obj.count: {{ obj.count }}</p>
        <button @click="incrementCount">Increment count</button>
    </div>

    <!-- Eager Watchers -->
    <div>
        <h3>Eager Watchers</h3>
        <p>source: {{ eagerValue }}</p>
        <button @click="changeEagerValue">Change eagerValue</button>
    </div>

    <!-- watchEffect() -->
    <div>
        <h3>watchEffect()</h3>
        <p>todoId: {{ todoId }}</p>
        <p>Data: {{ data }}</p>
        <button @click="changeTodoId">Change todoId</button>
    </div>
</template>