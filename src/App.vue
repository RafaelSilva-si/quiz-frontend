<template>
  <div id="quiz">
    <QuizTitle :text="'Questionário'" />
    <QuizProgress />
    <QuizTitle :text="'Pergunta 1'" />
    <QuizQuestion />
    <QuizButton />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import QuizProgress from "./components/QuizProgress.vue";
import QuizQuestion from "./components/QuizQuestion.vue";
import QuizButton from "./components/Utils/QuizButton.vue";
import QuizTitle from "./components/Utils/QuizTitle.vue";

export default defineComponent({
  name: "App",
  components: {
    QuizProgress,
    QuizQuestion,
    QuizButton,
    QuizTitle,
  },
});
</script>

<style>
body {
  font-family: "Lato", sans-serif;
  background-color: #f5f1e5;
}

#app {
  display: flex;
  flex: 1;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

@media (max-width: 600px) {
  body {
    padding: 0px 40px;
  }
}
</style>
