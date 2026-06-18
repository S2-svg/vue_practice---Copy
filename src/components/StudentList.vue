<template>
  <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4">
    <StudentCard
      v-for="item in students"
      :key="item.id"
      :student="item"
      @view-detail="(id) => emit('select-student', id)"
      @delete-student="(id) => emit('remove-student', id)"
    />
  </div>
</template>
<script setup>
import StudentCard from './StudentCard.vue'

// Task 2: Accepts the full students array from App.vue
defineProps({
  students: Array,
})

// Setup events to forward data back up to App.vue
const emit = defineEmits(['select-student', 'remove-student'])
</script>
