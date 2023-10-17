<template>
  <p v-bind:class="{ danger: hasError }">El mensaje se ha enviado correctamente</p>
  <p v-bind:class="{ danger: !hasError }">El mensaje no se ha enviado</p>
</template>

<script lang="ts" setup>
let hasError = false
</script>

<style>
.danger {
  color: red;
}
</style>
