<script setup>
import { Icon } from '@iconify/vue';
</script>

<template>
  <div class="about">
    <h1 style="margin-bottom: 20px;">About This Project</h1>
    <p style="margin-bottom: 25px;">
      This project is created by Dan Qu - based on John Komarnicki's Vue 3 Crash Course.
    </p>
    <a href="https://www.youtube.com/watch?v=KTFH4P8unUQ">
      Watch here
    </a>
    <div>
      <a href="https://github.com/wriggu/taskmanager-proto">
      <Icon
      class="pointer"
      icon="akar-icons:github-fill" width="18"
      style="animation: 1s cubic-bezier(0.14, 0.93, 0.6, 1.01) 0.2s 1 slideInBottom; margin-top:35%"
      />
      </a>
    </div>
    <p class="subtext" style="animation: 1s cubic-bezier(0.14, 0.93, 0.6, 1.01) 0.2s 1 slideInBottom; margin-top: 3px">
      Dan Qu ● STUDIO HAKU ● 2023
    </p>

  </div>
</template>

<style>
@keyframes slideInBottom {
  0% {
    transform: translateY(+75%);
    opacity: 0;
  }
  25% {
    opacity: 0;
  }
  75% {
    opacity: 80%;
  }
  100% {
    transform: translateY(0);
    opacity: 100%;
  }
}

a { 
  color: inherit; 
} 

.about {
  text-align: center;
  padding: 50px;
  margin: 20px;
  color: 191815;
  animation: 1s cubic-bezier(0.14, 0.93, 0.6, 1.01) 0s 1 slideInBottom;
}

.subtext {
  margin-bottom: 3px;
}

.pointer {
  cursor: pointer;
}
</style>
