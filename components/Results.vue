<template>
    <div>
      <h2>Scores:</h2>
      <p>Assertiveness: {{ scores.escape }}</p>
      <p>Self-Esteem: {{ scores.attack }}</p>
      <p>Empathy: {{ scores.manipulation }}</p>
      <p>Stress: {{ scores.assertiveness }}</p>
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
  