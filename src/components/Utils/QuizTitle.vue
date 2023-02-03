<template>
  <p class="title">{{ text }}</p>
</template>

<script>
export default {
  props: {
    text: { type: String, required: true },
  },
};
</script>

<style>
.title {
  font-size: 18px;
  margin-top: 40px;
  color: #e52729;
  font-weight: 600;
}
</style>
