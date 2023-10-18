<template>
  <section>
    <h3>Añadir profesor</h3>

    <div>
      <label>Nombres<input type="text" v-model="teacher.teacherName" /></label>
      <label>Apellidos<input type="text" v-model="teacher.teacherLastName" /></label>
      <label>DNI<input type="text" v-model="teacher.teacherDni" /></label>
      <label>Materias<input type="text" v-model="teacherSubject" /></label>
      <button @click="handleSubject()">Añadir materias</button>
      <ul>
        <li v-for="(i_subject, index) in teacher.teacherSubjects" v-bind:key="index">
          {{ i_subject }}
        </li>
      </ul>

      <input type="checkbox" v-model="teacher.teacherDocs" /> Documentación entregada
      <button @click="handleTeacher()">Añadir</button>
    </div>
  </section>

  <section>
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
  text-align: center;
}
</style>
