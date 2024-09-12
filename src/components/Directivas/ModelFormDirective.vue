<template>
  <form>
    <input type="text" v-model="inputText" />
    <p>{{ inputText }}</p>

    <input type="checkbox" v-model="inputCheck" /> Acepto los términos y
    condiciones.

    <select v-model="inputSelect">
      <option value="spain">Spain</option>
      <option value="uk">UK</option>
      <option value="france">France</option>
    </select>
  </form>
</template>

<script lang="ts" setup>
//"v-model", directiva bidireccional, para mandar o recibir datos en tiempo real mediante DOM
import { Ref, ref } from "vue"

let inputText: Ref = ref("")
let inputCheck: Ref = ref("true")
let inputSelect: Ref = ref("france")
</script>

<style scoped>
p {
  width: 300px;
  height: 300px;
  border: 1px solid black;
}
</style>
