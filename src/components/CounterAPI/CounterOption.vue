<template>
  <h3>Contador: {{ counter }}</h3>

  <button @click="addCounter">+</button>

  <button @click="dropCounter">-</button>
</template>

<script lang="ts">
//No necesitamos "ref" porque Option es más permisivo
import { defineComponent } from "vue"
export default defineComponent({
  name: "CounterOption",
  components: {},
  data() {
    let counter = 0
    return { counter }
  },
  methods: {
    addCounter() {
      this.counter++
    },
    dropCounter() {
      this.counter--
    }
  }
})
</script>

<style>
button {
  margin: 0px 2px;
}
</style>
