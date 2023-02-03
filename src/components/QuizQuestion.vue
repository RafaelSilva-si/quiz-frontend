<template>
  <div>
    <p class="question">What is the scientific name for modern day humans?</p>
    <form class="form">
      <QuisInput :placeholder="'Fit Description'" />
      <QuisInput :placeholder="'Fit Description'" />
      <QuisInput :placeholder="'Fit Description'" />
      <QuisInput :placeholder="'Fit Description'" />
    </form>
  </div>
</template>

<script>
import QuisInput from "./Utils/QuizInput.vue";

export default {
  components: {
    QuisInput,
  },
};
</script>

<style>
.question {
  font-size: 1.7rem;
  line-height: 1px;
}
.form {
  margin-bottom: 30px;
}

@media (max-width: 600px) {
  .question {
    line-height: normal;
  }
}
</style>
