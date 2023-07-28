<script setup>
import { RouterView } from "vue-router";
import TodoHeader from "./components/TodoHeader.vue";
window.onload = function() {document.body.scrollTop = document.documentElement.scrollTop = 0;};

</script>

<template>
  <TodoHeader />
  <RouterView />
</template>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Rubik:wght@300;400;500;700&display=swap");

* {
  font-family: 'Supreme', sans-serif;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  background-color: #FFFFE3;
  cursor: cell;
  scroll-behavior: smooth;
}

.container {
  max-width: 1100px;
  margin: 0 auto;
}
</style>
