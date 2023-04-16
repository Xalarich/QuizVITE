<script setup>
import { defineProps } from "vue";
import { RouterLink } from "vue-router";
const { questionStatus, barPercentage } = defineProps([
  "questionStatus",
  "barPercentage",
]);
</script>

<template>
  <header>
    <div id="home">
      <router-link to="/">
        <svg
          fill="#000000"
          width="35px"
          height="35px"
          viewBox="0 0 32 32"
          version="1.1"
          xmlns="http://www.w3.org/2000/svg"
        >
          <title>home</title>
          <path
            d="M0 14.016l2.016 1.984h4v14.016q0 0.832 0.576 1.408t1.408 0.576h4v-8q0-0.832 0.576-1.408t1.44-0.576h4q0.8 0 1.408 0.576t0.576 1.408v8h4q0.832 0 1.408-0.576t0.608-1.408v-14.016h4l1.984-1.984-16-14.016zM12 14.016q0-1.664 1.184-2.848t2.816-1.152 2.816 1.152 1.184 2.848-1.184 2.816-2.816 1.184-2.816-1.184-1.184-2.816z"
          ></path>
        </svg>
      </router-link>
    </div>
    <h2>{{ questionStatus }} questions</h2>
    <div class="completion-bar">
      <div class="completion" :style="{ width: barPercentage }"></div>
    </div>
  </header>
</template>

<style scoped>
* {
  padding: 0;
  margin: 0;
}
header {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-top: 3vh;
}
header h2 {
  font-size: 2.5rem;
}
.completion-bar {
  border: solid black 2px;
  width: 20vw;
  height: 5vh;
  margin-top: 2vh;
}
.completion {
  height: 100%;
  width: 0%;
  background-color: red;
}
#home {
  cursor: pointer;
  margin-right: 5vh;
  display: flex;
  align-self: flex-end;
}
</style>
