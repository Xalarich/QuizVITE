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
  <div id="container">
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
#container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 20px;
}
header {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
}

header h1 {
  font-size: 5rem;
  width: 100%;
  text-align: center;
}

header input {
  background-color: rgba(206, 206, 206, 0.45);
  border: none;
  border-radius: 5px;
  height: 30px;
  margin-top: 5px;
}
.quizes-container {
  height: 70vh;
  display: flex;
  justify-content: space-around;
}
@media (max-width: 1024px) {
  #container {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    gap: 20px;
    padding-bottom: 20px;
  }
  header {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: flex-start;
  }
  .quizes-container {
    display: flex;
    align-items: center;
    flex-direction: column;
    gap: 20px;
    height: max-content;
  }
}
</style>
