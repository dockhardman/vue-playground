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
import { ref } from 'vue'

const count = ref(0)
const text = ref('')

function increment() {
  count.value++
}
function onInput(e) {
  text.value = e.target.value
}
</script>

<template>
  <button v-on:click="increment">count is: {{ count }}</button>
  <br>
  <br>
  <input :value="text" @input="onInput" placeholder="Type here">
  <p>Input Text: {{ text }}</p>
</template>
