<template>
  <section class="section-form">
    <h3>Añadir profesor</h3>

    <div class="container">
      <div class="div-name">
        <label>Nombres</label>

        <input type="text" v-model="teacher.teacherName" />
      </div>

      <div class="div-last_name">
        <label>Apellidos</label>

        <input type="text" v-model="teacher.teacherLastName" />
      </div>

      <div class="div-dni">
        <label>DNI</label>

        <input type="text" v-model="teacher.teacherDni" />
      </div>

      <div class="div-subject">
        <label>Materias</label>

        <input type="text" v-model="teacherSubject" />

        <button @click="handleSubject()">Añadir materias</button>
      </div>

      <div class="div-list_subject">
        <ul>
          <li
            v-for="(i_subject, index) in teacher.teacherSubjects"
            v-bind:key="index"
          >
            {{ i_subject }}
          </li>
        </ul>
      </div>

      <div class="div-doc">
        <input type="checkbox" v-model="teacher.teacherDocs" /> Documentación
        entregada
      </div>

      <div class="div-register">
        <button @click="handleTeacher()">Registrar datos</button>
      </div>
    </div>
  </section>

  <section class="section-list">
    <h3>Listado de profesores</h3>

    <table>
      <tr>
        <th>Nombres</th>
        <th>Apellidos</th>
        <th>DNI</th>
        <th>Materias</th>
        <th>Documentación entregada</th>
      </tr>

      <tr v-for="i_teachers in teachers" v-bind:key="i_teachers.teacherDni">
        <th>{{ i_teachers.teacherName }}</th>
        <th>{{ i_teachers.teacherLastName }}</th>
        <th>{{ i_teachers.teacherDni }}</th>
        <th>
          <ul>
            <li
              v-for="(i_materias, index) in i_teachers.teacherSubjects"
              v-bind:key="index"
            >
              {{ i_materias }}
            </li>
          </ul>
        </th>
        <th v-if="i_teachers.teacherDocs">Entregada</th>
        <th v-else>No entregada</th>
      </tr>
    </table>
  </section>
</template>

<script lang="ts" setup>
import { Ref, ref } from "vue"

interface ITeacher {
  teacherName: string
  teacherLastName: string
  teacherDni: string
  teacherSubjects: Array<string>
  teacherDocs: boolean
}

//Tipado de datos por Typescript
let teacher: Ref<ITeacher> = ref({
  teacherName: "",
  teacherLastName: "",
  teacherDni: "",
  teacherSubjects: [],
  teacherDocs: false
})

let teachers: Ref<Array<ITeacher>> = ref([])
let teacherSubject: Ref<string> = ref("")

const handleSubject = () => {
  teacher.value.teacherSubjects.push(teacherSubject.value)

  teacherSubject.value = ""
}

const handleTeacher = () => {
  teachers.value.push({
    teacherName: teacher.value.teacherName,
    teacherLastName: teacher.value.teacherLastName,
    teacherDni: teacher.value.teacherDni,
    teacherSubjects: teacher.value.teacherSubjects,
    teacherDocs: teacher.value.teacherDocs
  })

  teacher.value.teacherName = ""
  teacher.value.teacherLastName = ""
  teacher.value.teacherDni = ""
  teacher.value.teacherSubjects = []
  teacher.value.teacherDocs = false
}
</script>

<style scoped>
* {
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

h3 {
  text-transform: uppercase;
  margin: 10px;
  text-align: center;
}

div {
  margin: 10px;
}

label,
button {
  display: block;
}

ul,
li {
  list-style-type: none;
  border: 0;
  padding: 0;
  margin: 0;
}

button {
  margin: 10px 0px;
}

table {
  border-collapse: collapse;
  width: 80%;
}

td,
th {
  border: 1px solid #000;
  text-align: center;
  padding: 8px;
}

.section-list {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
