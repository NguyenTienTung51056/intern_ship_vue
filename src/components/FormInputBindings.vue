<script setup>
import { ref, reactive } from 'vue'

const message = ref('')
const text = ref('')
const checked = ref(true)

const checkedNames = ref([])
const picked = ref('')

const selected = ref('')

const selectedMultiple = ref([])

const options = reactive([
    { text: 'One', value: 'A' },
    { text: 'Two', value: 'B' },
    { text: 'Three', value: 'C' }
])

const styleImportant = reactive({
    color: 'white',
    fontWeight: 'bold',
    backgroundColor: 'green !important'
})
</script>

<template>
    <h1>Form Input Bindings</h1>
    <div class="d-flex flex-column card shadow p-3 mb-5 bg-body rounded rounded border-0">
        <div class="m-2">
            <!-- this is a core concept of vue -->
            <input class="input-group-text" :value="text" @input="event => text = event.target.value">
        </div>
        <div class="m-2">
            <!-- //this is a simply way to do the same thing -->
            <input class="input-group-text" v-model="text" v-html="text">
        </div>

        <div class="m-2">
            <p>Message is: {{ message }}</p>
            <input class="input-group-text" v-model="message" placeholder="edit me" />
        </div>

        <div class="m-2">
            <span>Multiline message is:</span>
            <p style="white-space: pre-line;">{{ message }}</p>
            <textarea class="input-group-text" v-model="message" placeholder="add multiple lines"></textarea>
        </div>

        <div class="m-2">
            <!-- bad -->
            <span>bad:</span>
            <textarea class="input-group-text">{{ text }}</textarea>

            <!-- good -->
            <span>good:</span>
            <textarea class="input-group-text" v-model="text"></textarea>
        </div>

        <div class="m-2">
            <h3>checkbox</h3>
            <div class="d-flex flex-column card w-25 justify-content-center align-items-center shadow p-3 mb-5 bg-body rounded rounded border-0"
                :style="[checked ? styleImportant : '']">
                <input class="input-group-text w-25" type="checkbox" id="checkbox" v-model="checked" />
                <label for="checkbox">{{ checked }}</label>
            </div>
        </div>

        <div class="m-2 form-check d-flex flex-column">
            <div>Checked names:
                <ul>
                    <li v-for="item in checkedNames" :key="item">
                        {{ item }}
                    </li>
                </ul>
            </div>


            <input class="form-check-input" type="checkbox" id="jack" value="Jack" v-model="checkedNames">
            <label class="form-check-label" for="jack">Jack</label>

            <input class="form-check-input" type="checkbox" id="john" value="John" v-model="checkedNames">
            <label class="form-check-label" for="john"> John </label>

            <input class="form-check-input" type="checkbox" id="mike" value="Mike" v-model="checkedNames">
            <label class="form-check-label" for="mike">Mike</label>
        </div>


        <div class="m-2 form-check d-flex flex-column">
            <div>Picked: {{ picked }}</div>

            <input type="radio" id="one" value="One" v-model="picked" />
            <label for="one">One</label>

            <input type="radio" id="two" value="Two" v-model="picked" />
            <label for="two">Two</label>

        </div>

        <div class="m-2 form-check d-flex flex-column">
            <div>Selected: {{ selected }}</div>

            <!-- Single select -->
            <select v-model="selected">
                <option disabled value="">Please select one</option>
                <option>A</option>
                <option>B</option>
                <option>C</option>
            </select>

            <!-- Multiple select (bound to array) -->
            <select v-model="selectedMultiple" multiple>
                <option>A</option>
                <option>B</option>
                <option>C</option>
            </select>
            <div>Selected: {{ selectedMultiple }}</div>

            <!-- Dynamically rendered options with v-for -->
            <select v-model="selectedDynamic">
                <option v-for="option in options" :value="option.value">
                    {{ option.text }}
                </option>
            </select>
            <div>Selected: {{ selectedDynamic }}</div>
        </div>
    </div>
</template>