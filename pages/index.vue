<!-- index.vue -->
<template>
    <div>
      <h1 class="font-bold">Autodiagnostic d'assertivité</h1>
      <h2>Formulaire</h2>
      <Form @submit="handleScores"/>
      <Results v-if="submitted" :scores="scores" />
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  import QuestionForm from '@/components/Form.vue';
  import ScoreResult from '@/components/Results.vue';
  
  let scores = ref({});
  let submitted = ref(false);
  
  const handleScores = (newScores) => {
      scores.value = newScores;
      submitted.value = true;
  }
  </script>
  
  <style scoped>
  h1{
      font-size: 36px;
      margin-bottom: 20px;
  }
  h2{
      font-size: 24px;
      margin-bottom: 20px;
  }
  </style>
  