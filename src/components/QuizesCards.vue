<script setup>
import { useRouter } from "vue-router";
import { defineProps } from "vue";

const router = useRouter();
const { quiz } = defineProps(["quiz"]);

const navigateToQuiz = () => {
  router.push(`/quiz/${quiz.id}`);
};
</script>
<template>
  <div class="card-container">
    <div class="card" @click="navigateToQuiz">
      <img :src="quiz.img" :alt="quiz.name" />
      <h4>{{ quiz.name }}</h4>
      <p>{{ quiz.questions.length }} questions</p>
    </div>
  </div>
</template>

<style scoped>
.card {
  overflow: hidden;
  border: 2px solid black;
  text-align: center;
  font-size: 1.5rem;
  cursor: pointer;
}

.card img {
  padding: 2%;
  width: 80%;
}

.card-container {
  width: 30%;
}
</style>
