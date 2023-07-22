<template>
    <div class="bg-white shadow-md rounded p-6 mb-4">
      <h2 class="text-xl font-semibold mb-4">Scores</h2>
      <div class="grid grid-cols-4 justify-items-center">
        <p class="mb-2"><span class="font-bold">Attitude de fuite passive:</span> {{ scores.escape }}</p>
        <p class="mb-2"><span class="font-bold">Attitude d'attaque agressive:</span> {{ scores.attack }}</p>
        <p class="mb-2"><span class="font-bold">Attitude de manipulation:</span> {{ scores.manipulation }}</p>
        <p class="mb-2"><span class="font-bold">Attitude assertive:</span> {{ scores.assertiveness }}</p>
    </div>
    </div>
  </template>
  
  <script setup>
  const props = defineProps({
    scores: {
      type: Object,
      required: true
    }
  });
  </script>
  