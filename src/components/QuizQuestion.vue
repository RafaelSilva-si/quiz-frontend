<template>
  <div class="form-element">
    <p class="question">{{ question.question }}</p>
    <form class="form" @submit="(e) => this.$emit('next', e)">
      <div class="aswnser">
        <QuisInput
          v-for="(answers, i) in question.answers"
          :key="i"
          :placeholder="answers"
          :value="answers"
          :checked="question.aswnser == answers"
        />
      </div>
      <a @click="this.$emit('back')" class="btn_back" v-if="current >= 1"
        >Voltar</a
      >
      <QuizButton :title="'Avançar'" v-if="current <= 18" />
    </form>
  </div>
</template>

<script>
import QuisInput from "./Utils/QuizInput.vue";
import QuizButton from "./Utils/QuizButton.vue";

export default {
  components: {
    QuisInput,
    QuizButton,
  },
  data() {
    return { feedback: "" };
  },
  props: {
    question: { type: Object, required: true },
    current: { type: Number, required: true },
  },
};
</script>

<style>
.form-element {
  min-height: 200px;
}
.aswnser {
  min-height: 100px;
}
.question {
  font-size: 1.2rem;
  margin-top: -10px;
  text-align: justify;
}
.form {
  margin-bottom: 30px;
}

.btn_back {
  cursor: pointer;
}

@media (max-width: 600px) {
  .form-element {
    min-height: 300px;
  }
}
</style>
