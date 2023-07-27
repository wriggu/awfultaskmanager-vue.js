<template>
  <div class="about">
    <h1 style="margin-bottom: 20px;">About This Project</h1>
    <p style="margin-bottom: 25px;">
      This project is created by Dan Qu - based on John Komarnicki's Vue 3 Crash Course.
    </p>
    <a
      href="https://www.youtube.com/watch?v=KTFH4P8unUQ"
      >Watch here</a>
    <p class="subtext" style="animation: 1s cubic-bezier(0.14, 0.93, 0.6, 1.01) 0.13s 1 slideInBottom; margin-top: 50%">
      Dan Qu ● STUDIO HAKU ● 2023
    </p>
    <a class="subtext">

    </a>
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
</style>
