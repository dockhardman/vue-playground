<!--
App (root component)
├─ TodoList
│  └─ TodoItem
│     ├─ TodoDeleteButton
│     └─ TodoEditButton
└─ TodoFooter
   ├─ TodoClearButton
   └─ TodoStatistics
-->
<script setup>
import { nextTick, ref, reactive } from 'vue'

const count = ref(0)
const text = ref('')
const awesome = ref(true)
const obj = reactive({
  nested: { count: 0 },
  arr: ['foo', 'bar']
})
const author = reactive({
  name: 'John Doe',
  books: [
    'Vue 2 - Advanced Guide',
    'Vue 3 - Basic Guide',
    'Vue 4 - The Mystery'
  ]
})
const parentMessage = 'Parent'
const messages = reactive([{ message: 'Foo' }, { message: 'Bar' }])

function increment() {
  count.value++
  nextTick(() => {
    // access updated DOM
  })
}
function onInput(e) {
  text.value = e.target.value
}
function mutateDeeply() {
  obj.nested.count++
  obj.arr.push('baz')
}
function calculateBooksMessage() {
  return author.books.length > 0 ? 'Yes' : 'No'
}
function now() {
  return Date.now()
}
</script>

<template>
  <button v-on:click="increment">count is: {{ count }}</button>
  <br>
  <br>
  <input :value="text" @input="onInput" placeholder="Type here">
  <p>Input Text: {{ text }}</p>
  <br>
  <button v-on:click="mutateDeeply">obj count is: {{ obj }}</button>
  <br>
  <br>
  <p>Has published books:</p>
  <span>{{ calculateBooksMessage() }} {{ now() }}</span>
  <br>
  <br>
  <button @click="awesome = !awesome">Toggle</button>
  <h1 v-if="awesome">Vue is awesome!</h1>
  <h1 v-else>Oh no 😢</h1>
  <br>
  <li v-for="(message, index) in messages">
    {{ parentMessage }} - {{ index }} - {{ message.message }}
  </li>
</template>
