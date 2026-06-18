<template>
  <BaseCard>
    <div class="text-center">
      <img :src="student.image" class="w-20 h-20 rounded-full mx-auto object-cover mb-2" />

      <h3 class="text-lg font-bold text-gray-800">{{ student.name }}</h3>
      <p class="text-sm text-gray-500 mb-4">Major: {{ student.major }}</p>

      <div class="flex gap-2 justify-center">
        <button
          @click="emit('view-detail', student.id)"
          class="bg-emerald-500 text-white text-xs px-3 py-1.5 rounded hover:bg-emerald-600"
        >
          View Detail
        </button>

        <button
          @click="emit('delete-student', student.id)"
          class="bg-red-500 text-white text-xs px-3 py-1.5 rounded hover:bg-red-600"
        >
          Delete
        </button>
      </div>
    </div>
  </BaseCard>
</template>

<script setup>
import BaseCard from './BaseCard.vue'

// Task 2: Accepts one student object from the parent component
defineProps({
  student: Object,
})

// Task 3 & Bonus Task: Listens to button clicks and prepares events
const emit = defineEmits(['view-detail', 'delete-student'])
</script>
