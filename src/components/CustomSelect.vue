<template>
  <div class="wrap">
    <div class="select-custom" id="select">
      <div class="select__input">input</div>
      <div class="select__dropdown">dropdown</div>
    </div>
  </div>
</template>

<script>
export default {
  methods: {},
}
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Bad+Script&family=Roboto:wght@300;400&display=swap");
@import "../_variabels.css";
@import "../_animation.css";

.wrap {
  width: var(--button-width);
}
.select-custom {
  position: relative;
  width: 100%;
  z-index: 100;
}
.select__input {
  display: flex;
  justify-content: center;
  align-items: center;
  height: var(--button-height);
  width: var(--button-width);
  margin-top: 34px;
  color: var(--select-color);
  font-size: var(--button-font-size);
  line-height: var(--button-line-height);
  font-weight: var(--normal-font-weight);
  border-radius: var(--button-border-radius);
  border: none;
  background: var(--select-main-gradient);
  box-shadow: var(--select-shadow);
  cursor: pointer;
  overflow: hidden;
}
.select__dropdown {
  position: absolute;
  width: var(--button-width);
  height: 100px;
  background: var(--select-main-gradient);
  border-radius: 0 0 var(--button-border-radius) var(--button-border-radius);
  overflow-y: auto;
}
</style>
