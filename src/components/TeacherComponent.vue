<template>
  <h1 class="h1-title">Control de docentes</h1>

  <form>
    <div class="div-input-text">
      <input type="text" placeholder="Nombres" v-model="name" /> <br />
      <input type="text" placeholder="Apellidos" v-model="last_name" /> <br />
      <input type="text" placeholder="DNI" v-model="dni" />
    </div>

    <select class="select-option" v-model="inputSelect">
      <option value="Matemáticas">Matemáticas</option>
      <option value="Inglés">Inglés</option>
      <option value="Programación I">Programación I</option>
      <option value="Algoritmos">Algoritmos</option>
      <option value="Introducción a la Ingenieria">
        Introducción a la Ingenieria
      </option>
    </select>

    <br />

    <input type="checkbox" v-model="inputCheck" /> ¿Subió toda la documentación a la
    web?
  </form>

  <div class="div-table">
    <h2>Profesores registrados</h2>

    <table class="table">
      <tr>
        <th>Nombres</th>
        <th>Apellidos</th>
        <th>DNI</th>
        <th>Materia</th>
        <th>Documentación</th>
      </tr>

      <tr>
        <th>{{ name }}</th>
        <th>{{ last_name }}</th>
        <th>{{ dni }}</th>
        <th>{{ inputSelect }}</th>
        <th>{{ inputCheck }}</th>
      </tr>
    </table>
  </div>
</template>

<script lang="ts" setup>
import { Ref, ref } from "vue"

let name: Ref = ref("")
let last_name: Ref = ref("")
let dni: Ref = ref("")

let inputSelect: Ref = ref("")

let inputCheck: Ref = ref("")

const checkConvert = () => {
  if (inputCheck.value) {
    inputCheck.value = "Sí"
  } else {
    inputCheck.value = "No"
  }
}
</script>

<style scoped>
* {
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  text-align: center;
}

.h1-title {
  text-transform: uppercase;
}

input,
div {
  margin: 5px 0px;
}

.div-table {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.table {
  width: 80%;
  text-align: center;
  align-items: center;
  border-collapse: collapse;
}

td,
th {
  border: 1px solid black;
  text-align: center;
  padding: 8px;
}
</style>
