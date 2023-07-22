<!-- index.vue -->
<template>
    <div>
      <h1 class="font-bold">Autodiagnostic d'assertivité</h1>
      <h2>Formulaire</h2>
      <p class="pb-4">Répondez spontanément aux questions :<br>
- Plutôt vrai : si vous pensez ou agissez de cette façon la plupart du temps,<br>
- Plutôt faux : si vous ne faites ou ne pensez que rarement ce qui est décrit.</p>
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
  