<script setup lang="ts">
import StudentCard from '../components/studentCard.vue'
import type { StudentItem } from '@/type'
import { type Ref, ref } from 'vue'
import StudentService from '@/services/StudentService'

const studentList: Ref<Array<StudentItem>>=ref([])
  
StudentService.getEvent().then((response) => {
  studentList.value = response.data

})
</script>

<template>
  <main class="events">
    <StudentCard v-for="student in studentList" :key="student.id" :student="student"></StudentCard>
  </main>
</template>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
