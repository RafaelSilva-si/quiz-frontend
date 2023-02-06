<template>
  <div id="quiz">
    <div v-if="questions.length > 0 && question <= questions.length - 1">
      <QuizTitle :text="'Questionário'" />
      <QuizProgress :progress="progress" :question="question" />
      <QuizTitle :text="`Pergunta ${question + 1}`" />
      <div v-for="(q, i) in questions" :key="i" :question="q">
        <aside v-if="i == question">
          <QuizQuestion
            :question="q"
            :current="question"
            @next="(e:any)=>next(e)"
            @back="back"
          />
        </aside>
      </div>
      <a @click="back" class="btn_back" v-if="question > 18">Voltar</a>
      <QuizButton :title="'Finalizar'" v-if="question > 18" @click="submit" />
    </div>
    <div v-else-if="questions.length > 0" class="feedback">
      <h1>Seu Resultado foi</h1>
      <h2>{{ hits }}%</h2>
      <QuizButton :title="'Reiniciar'" @click="finish" />
    </div>
    <div v-if="questions.length <= 0" class="feedback">
      <h1>
        Erro ao carregar quiz, verifique se a api está rodando na porta 3000
      </h1>
      <QuizButton :title="'Recarregar'" @click="finish" />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import QuizProgress from "./components/QuizProgress.vue";
import QuizQuestion from "./components/QuizQuestion.vue";
import QuizButton from "./components/Utils/QuizButton.vue";
import QuizTitle from "./components/Utils/QuizTitle.vue";
import axios from "axios";

export default defineComponent({
  name: "App",
  data() {
    interface Question {
      category: string;
      type: string;
      difficulty: string;
      question: string;
      correct_answer: string;
      incorrect_answers: Array<string>;
      aswnser?: string;
    }
    return {
      hits: 0,
      question: 0,
      questions: [] as Question[],
    };
  },
  computed: {
    progress(): number {
      const total = this.questions.length;
      return Math.round((this.question / total) * 100) || 0;
    },
  },
  components: {
    QuizProgress,
    QuizQuestion,
    QuizButton,
    QuizTitle,
  },
  mounted() {
    axios
      .get("http://localhost:3000/questions/1")
      .then((response) => (this.questions = response.data));
  },
  methods: {
    next(e: {
      preventDefault: () => void;
      target: { aswnser: { value: string | undefined } };
    }) {
      e.preventDefault();
      this.questions[this.question].aswnser = e.target.aswnser.value;
      this.question < 20 && this.question++;
    },
    submit() {
      const aswnser = this.questions.filter(
        (i) => i.aswnser == i.correct_answer
      ).length;
      this.question++;
      this.hits = Math.round((aswnser / this.questions.length) * 100) || 0;
    },
    finish() {
      window.location.reload();
    },
    back() {
      this.question--;
    },
  },
});
</script>

<style>
body {
  font-family: "Lato", sans-serif;
  background-color: #f5f1e5;
}

.feedback {
  text-align: center;
}

#app {
  display: flex;
  flex: 1;
  flex-direction: column;
  justify-content: center;
  height: 100vh;
  max-width: 940px;
  margin: 0 auto;
}

@media (max-width: 600px) {
  body {
    padding: 0px 40px;
  }
}
</style>
