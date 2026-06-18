<template>
  <div class="fixed inset-0 bg-black bg-opacity-40 flex justify-center items-center p-4 z-50">
    <div class="bg-white rounded-lg p-6 max-w-sm w-full text-center shadow-lg">
      <h2 class="text-xl font-bold text-gray-900 mb-2">Student Information</h2>
      <div class="border-b border-gray-200 mb-4"></div>

      <img :src="student.image" class="w-24 h-24 rounded-full mx-auto object-cover mb-4" />
      <div class="text-left bg-gray-50 p-4 rounded mb-4 text-sm space-y-1">
        <p><strong>Name:</strong> {{ student.name }}</p>
        <p><strong>Age:</strong> {{ student.age }}</p>
        <p><strong>Major:</strong> {{ student.major }}</p>
      </div>

      <button
        @click="$emit('close')"
        class="bg-gray-700 text-white w-full py-2 rounded text-sm hover:bg-gray-800"
      >
        Close
      </button>
    </div>
  </div>
</template>

<script setup>
// Task 2: Accepts the single selected student's deeper profile data
defineProps({
  student: Object,
})

defineEmits(['close'])
</script>
