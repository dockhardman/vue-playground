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
const obj = reactive({
  nested: { count: 0 },
  arr: ['foo', 'bar']
})

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
</script>

<template>
  <button v-on:click="increment">count is: {{ count }}</button>
  <br>
  <br>
  <input :value="text" @input="onInput" placeholder="Type here">
  <p>Input Text: {{ text }}</p>
  <br>
  <button v-on:click="mutateDeeply">obj count is: {{ obj }}</button>
</template>
