<template>
  <div class="progress-container">
    <div class="progress">
      <div class="progress-bar" :style="{ width: 30 + '%' }"></div>
    </div>
    <p class="questionIndicator">Pergunta 1 de 20</p>
  </div>
</template>

<script>
export default {};
</script>

<style>
.progress {
  width: 500px;
  height: 10px;
  border-radius: 50px;
  background-color: #d1d5db;
}

.progress-bar {
  width: 500px;
  height: 10px;
  border-radius: 50px;
  background-color: #e52729;
}
</style>
