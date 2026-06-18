<template>
  <div class="min-h-screen bg-gray-50 p-6 md:p-12">
    <div class="max-w-5xl mx-auto">
      <h1 class="text-3xl font-black text-center text-gray-800 mb-8">Student Directory</h1>

      <StudentList
        :students="students"
        @select-student="handleViewDetail"
        @remove-student="handleDeleteStudent"
      />

      <StudentDetail
        v-if="selectedStudent"
        :student="selectedStudent"
        @close="selectedStudent = null"
      />
    </div>
  </div>
</template>
<script setup>
import { ref } from 'vue'
import StudentList from './components/StudentList.vue'
import StudentDetail from './components/StudentDetail.vue'

// Sample Data Setup inside reactive ref array
const students = ref([
  {
    id: 1,
    name: 'Dara',
    age: 20,
    major: 'Web Development',
    image: 'https://i.pravatar.cc/150?img=1',
  },
  { id: 2, name: 'Sokha', age: 21, major: 'Networking', image: 'https://i.pravatar.cc/150?img=2' },
  {
    id: 3,
    name: 'Vanna',
    age: 19,
    major: 'Graphic Design',
    image: 'https://i.pravatar.cc/150?img=3',
  },
  {
    id: 4,
    name: 'Nita',
    age: 22,
    major: 'Software Engineering',
    image: 'https://i.pravatar.cc/150?img=4',
  },
])

// Tracks which student profile is currently clicked/selected
const selectedStudent = ref()

// Task 3: Triggered when "View Detail" event comes up from children components
const handleViewDetail = (id) => {
  const match = students.value.find((s) => s.id === id)
  if (match) {
    selectedStudent.value = match
  }
}

// Bonus Task: Triggered when "Delete" event comes up from children components
const handleDeleteStudent = (id) => {
  students.value = students.value.filter((s) => s.id !== id)

  // Close the popup info card if that specific student record gets deleted
  if (selectedStudent.value && selectedStudent.value.id === id) {
    selectedStudent.value = null
  }
}
</script>
