<template>
    <form @submit.prevent="calculateScore" class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4 flex flex-col">
      <div v-for="(question, index) in questions" :key="index" class="mb-4">
        <label :for="'question' + index" class="block text-gray-700 text-sm font-bold mb-2">{{ question.text }}</label>
        <div class="mt-2">
          <label :for="'question' + index" class="inline-flex items-center">
            <input type="radio" :id="'question' + index" :name="'question' + index" value="true" v-model="answers[question.id]" class="form-radio">
            <span class="ml-2">Vrai</span>
          </label>
          <label :for="'question' + index" class="inline-flex items-center ml-6">
            <input type="radio" :id="'question' + index" :name="'question' + index" value="false" v-model="answers[question.id]" class="form-radio">
            <span class="ml-2">Faux</span>
          </label>
        </div>
      </div>
      <button type="submit" class="btn mx-auto">Valider</button>
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
  