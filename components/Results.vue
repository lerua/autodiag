<template>
    <div>
      <h2>Scores:</h2>
      <p>Assertiveness: {{ scores.assertiveness }}</p>
      <p>Self-Esteem: {{ scores.selfEsteem }}</p>
      <p>Empathy: {{ scores.empathy }}</p>
      <p>Stress: {{ scores.stress }}</p>
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
  