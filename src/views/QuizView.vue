<script setup>
import Header from "../components/QuizHeader.vue";
import Question from "../components/Question.vue";
import Result from "../components/Result.vue";
import quizes from "../data/quizes.json";
import { useRoute } from "vue-router";
import { computed } from "vue";
import { ref } from "vue";

const route = useRoute();

const quizId = parseInt(route.params.id);

const quiz = quizes.find((q) => q.id === quizId);

const currentQuestionIndex = ref(0);

const numberOfCorrectAnswers = ref(0);

const showResults = ref(false);

const questionStatus = computed(() => {
  return `${currentQuestionIndex.value}/${quiz.questions.length}`;
});

const barPercentage = computed(
  () => `${(currentQuestionIndex.value / quiz.questions.length) * 100}%`
);

const onOptionSelected = (isCorrect) => {
  if (isCorrect) {
    numberOfCorrectAnswers.value++;
  }
  if (quiz.questions.length - 1 === currentQuestionIndex.value) {
    showResults.value = true;
  }
  currentQuestionIndex.value++;
};

const increaseIndexTwo = () => {
  currentQuestionIndex.value++;
  if (quiz.questions.length === currentQuestionIndex.value) {
    showResults.value = true;
  }
};
</script>

<template>
  <div>
    <Header :questionStatus="questionStatus" :barPercentage="barPercentage" />
    <div>
      <Question
        v-if="!showResults"
        :question="quiz.questions[currentQuestionIndex]"
        @selectOption="onOptionSelected"
        @increaseIndex="increaseIndexTwo"
      />
      <Result
        v-else
        :numberOfCorrectAnswers="numberOfCorrectAnswers"
        :quiz="quiz"
      />
    </div>
  </div>
</template>

<style scoped></style>
