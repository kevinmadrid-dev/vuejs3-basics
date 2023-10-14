<template>
  <h3>Contador: {{ counter }}</h3>
  <button @click="addCounter">+</button>
  <button @click="dropCounter">-</button>
</template>

<script lang="ts">
//Para reflejar los cambios mediante DOM, debemos usar "ref"
//Al usar Typescript debemos indicar los tipos de datos "Ref" y "void"
import { defineComponent, Ref, ref } from "vue"
export default defineComponent({
  name: "CounterComposition",
  components: {},
  setup() {
    let counter: Ref = ref(0)
    const addCounter = () => {
      counter.value++
    }
    const dropCounter = (): void => {
      counter.value--
    }
    return { counter, addCounter, dropCounter }
  }
})
</script>
