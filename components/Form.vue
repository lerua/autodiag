<template>
    <form @submit.prevent="calculateScore">
      <div v-for="(question, index) in questions" :key="index">
        <label :for="'question' + index">{{ question.text }}</label>
        <input type="radio" :id="'question' + index" :name="'question' + index" value="true" v-model="answers[question.id]" required>
        <label :for="'question' + index">Vrai</label>
        <input type="radio" :id="'question' + index" :name="'question' + index" value="false" v-model="answers[question.id]" required>
        <label :for="'question' + index">Faux</label>
      </div>
      <button type="submit" class="btn m-4">Valider</button>
    </form>
  </template>
  
  <script setup>
  import { ref, reactive } from 'vue';
  import questionsData from './questions.js'; // import the questions
  let questions = ref(questionsData);

  let answers = reactive({
      q1: '',
      q2: '',
      q3: '',
      q4: ''
  });
  
  let scores = reactive({
      escape: 0,
      attack: 0,
      manipulation: 0,
      assertiveness: 0
  });

  const reset = () => {
    for (const score in scores) {
        scores[score] = 0;
    }
}

  const emit = defineEmits(['submit']);

  const calculateScore = () => {
    reset();
      for (const question of questions.value) {
          if (answers[question.id] === "true") {
              scores[question.score]++;
          }
      }  
      emit('submit', scores);
    }
  </script>
  