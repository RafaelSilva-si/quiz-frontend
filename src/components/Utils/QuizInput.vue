<template>
  <label class="container"
    >{{ placeholder }}
    <input type="radio" name="aswnser" :value="value" :checked="checked" />
    <span class="checkmark"></span>
  </label>
</template>

<script>
export default {
  props: ["placeholder", "value", "checked"],
};
</script>

<style>
.container {
  display: block;
  position: relative;
  padding-left: 25px;
  margin-bottom: 12px;
  cursor: pointer;
  font-size: 16px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

.container input {
  position: absolute;
  opacity: 0;
  cursor: pointer;
  height: 0;
  width: 0;
}

.checkmark {
  position: absolute;
  top: 0;
  left: 0;
  height: 15px;
  width: 15px;
  margin-top: 2px;
  background-color: #fff1;
  border: 1px solid #e52729;
  border-radius: 50%;
}

.container:hover input ~ .checkmark {
  background-color: #e52729;
}

.container input:checked ~ .checkmark {
  background-color: #e52729;
}
</style>
