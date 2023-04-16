<script setup>
import QuizesCards from "../components/QuizesCards.vue";
import quizes from "../data/quizes.json";

import { ref, watch } from "vue";

const qs = ref(quizes);
const search = ref("");

watch(search, () => {
  qs.value = quizes.filter((quiz) =>
    quiz.name.toLowerCase().includes(search.value.toLowerCase())
  );
});
</script>

<template>
  <div>
    <header>
      <h1>Quizes</h1>
      <input v-model.trim="search" type="text" placeholder="search..." />
    </header>
    <div class="quizes-container">
      <QuizesCards v-for="quiz in qs" :key="quiz.id" :quiz="quiz" />
    </div>
  </div>
</template>

<style scoped>
.quizes-container {
  display: flex;
  height: 70vh;
  justify-content: space-around;
}

header {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
}

header h1 {
  font-size: 5rem;
}

header input {
  margin-left: 30px;
  background-color: rgba(206, 206, 206, 0.45);
  border: none;
  border-radius: 5px;
  height: 30px;
  margin-top: 5px;
}
</style>
