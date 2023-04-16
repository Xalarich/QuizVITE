<script setup>
import { defineProps, defineEmits } from "vue";

const { question } = defineProps(["question"]);

const emit = defineEmits(["selectOption", "increaseIndex"]);

const emitSelectedOption = (isCorrect) => {
  emit("selectOption", isCorrect);
};
const emitIncreaseInIndex = (event) => {
  emit("increaseIndex", event);
};
</script>

<template>
  <div class="container">
    <div class="question">
      <p>{{ question.text }}</p>
    </div>
    <div
      v-for="option in question.options"
      :key="option.id"
      class="option"
      @click="emitSelectedOption(option.isCorrect)"
    >
      <p class="selector">{{ option.label }}</p>
      <p class="answer">{{ option.text }}</p>
    </div>
    <button @click="emitIncreaseInIndex(event)">Next Question</button>
  </div>
</template>

<style scoped>
.container {
  margin-top: 6vh;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.question {
  font-size: 2rem;
  text-align: center;
}
.option {
  display: flex;
  font-size: 1.5rem;
  margin-top: 1rem;
  border: solid black 0.2em;
  cursor: pointer;
  text-align: center;
}
.selector {
  border-right: solid black 0.2em;
  padding: 0 1rem 0 1rem;
  display: flex;
}
.answer {
  padding: 0 1rem 0 1rem;
}
button {
  border-style: none;
  margin: 15px 0 10px 0;
  border: solid black 0.2em;
  cursor: pointer;
  font-size: 1.2rem;
  font-family: "Roboto", sans-serif;
  background-color: white;
}
</style>
