<template>
  <h2 v-if="age >= 18">Eres mayor de edad</h2>
  <h2 v-else-if="age < 18">Eres menor de edad</h2>
</template>

<script lang="ts" setup>
//Directivas: Preposición "v-" en las etiquetas
//"v-if" solo renderiza en el DOM la etiqueta que cumple con la directiva. Uso: Cambios puntuales
//"v-show" renderiza todas las opciones, pero solo muestra la correcta. Uso: Cambios continuos
let age = 11
</script>

<style scope></style>
