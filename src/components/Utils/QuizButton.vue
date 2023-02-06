<template>
  <button class="button">{{ title }}</button>
</template>

<script>
export default {
  props: ["title"],
};
</script>

<style>
.button {
  border: none;
  border-radius: 15px;
  background-color: #e52729;
  color: #fff;
  height: 50px;
  width: 90px;
  margin: 10px;
}

@media (max-width: 600px) {
  .button {
    width: 100%;
  }
}
</style>
