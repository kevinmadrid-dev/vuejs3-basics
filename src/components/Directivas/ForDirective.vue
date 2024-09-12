<template>
  <ul>
    <li v-for="country in countries" v-bind:key="country.code">
      {{ country.name }}
    </li>
  </ul>
</template>

<script lang="ts" setup>
//v-bind:key="", es el identificador único para el for. v-bind:key === :key
import { Ref, ref } from "vue"

interface ICountry {
  code: string
  name: string
}

let countries: Ref<Array<ICountry>> = ref([
  { code: "es", name: "Spain" },
  { code: "en", name: "UK" },
  { code: "fr", name: "France" },
  { code: "it", name: "Italy" },
  { code: "pt", name: "Portugal" }
])
</script>

<style></style>
