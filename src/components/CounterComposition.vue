<template>
  <h3>Contador: {{ counter }}</h3>
  <button @click="addCounter">+</button>
  <button @click="dropCounter">-</button>
</template>

<script lang="ts" setup>
//Para reflejar los cambios mediante DOM, debemos usar "ref"
//Al usar Typescript debemos indicar los tipos de datos "Ref" y "void"
import { Ref, ref } from "vue"

let counter: Ref = ref(0)
const addCounter = (): void => {
  counter.value++
}
const dropCounter = (): void => {
  counter.value--
}
</script>
