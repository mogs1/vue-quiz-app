<template>
    <div class="flex gap-2 mb-4 justify-center">
      <div
        v-for="n in total"
        :key="n"
        class="h-2 w-10 rounded-full"
        :class="n <= step ? 'bg-blue-600' : 'bg-gray-300'"
      />
    </div>
  </template>
  
  <script setup>
  const props = defineProps({
    step: Number,
    total: Number,
  });
  </script>
  