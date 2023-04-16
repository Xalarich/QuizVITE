<script setup>
import { defineProps } from "vue";

const { numberOfCorrectAnswers, quiz } = defineProps([
  "numberOfCorrectAnswers",
  "quiz",
]);
</script>

<template>
  <div class="results">
    <h1>
      You have answered {{ numberOfCorrectAnswers }} out of
      {{ quiz.questions.length }} correctly!
    </h1>
  </div>
</template>
<style scoped>
.results {
  display: flex;
  align-items: center;
  justify-content: center;
}
h1 {
  text-align: center;
}
</style>
