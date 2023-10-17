<template>
  <p v-bind:class="{ danger: hasError }">El mensaje se ha enviado correctamente</p>
  <p v-bind:class="{ danger: !hasError }">El mensaje no se ha enviado</p>

  <p v-bind:style="{ backgroundColor: 'black', color: 'red' }">
    El mensaje se ha enviado correctamente
  </p>

  <p v-bind:style="{ backgroundColor: bgcValue, color: colorValue }">Text</p>

  <button @click="changeColor()">Cambiar color</button>
</template>

<script lang="ts" setup>
import { ref } from "vue"

let hasError = false
let bgcValue = ref("#fff")
let colorValue = ref("#000")
let darkMode = ref(false)

const changeColor = () => {
  darkMode.value = !darkMode.value
  if (darkMode.value) {
    bgcValue.value = "#000"
    colorValue.value = "#fff"
  } else {
    bgcValue.value = "#fff"
    colorValue.value = "#000"
  }
}
</script>

<style>
.danger {
  color: red;
}
</style>
