<template>
    <div class="p-6 text-center">
      <h1 class="text-2xl font-bold mb-4">🎉 Great Job!</h1>
      <p class="mb-2">Let's see what you got this time</p>
      <button @click="restartGame" class="mt-4 bg-green-600 text-white px-4 py-2 rounded">
        🔁 Restart
      </button>
    </div>
  </template>
  
  <script setup>
  const props = defineProps(['restartGame']);
  </script>
  