<script setup>
import { RouterLink } from 'vue-router';
</script>

<template>
  <header>
    <nav class="container">
      <div class="branding">
        <h1><RouterLink to="/" style="text-decoration: none; color: inherit;">.ksatlufwa</RouterLink></h1>
      </div>    
      <ul class="nav-routes">
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </ul>
    </nav>
  </header>
</template>


<style lang="scss" scoped>
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

header {
  nav {
    max-width: 90%;
    display: flex;
    padding: 21px 13px;
    align-items: center;

    .branding {
      display: flex;
      align-items: center;

      h1 {
        font-size: 24px;
        color: #191815;
        margin-top: 0px;
        margin-bottom: 0px;
        animation: 1s cubic-bezier(0.14, 0.93, 0.6, 1.01) 0s 1 slideInBottom;
      }
    }

    .nav-routes {
      font-weight: 500;
      display: flex;
      flex: 1;
      justify-content: flex-end;
      gap: 12px;
      list-style: none;
      color: #191815;
      margin-bottom: 0px;
      margin-top: 0px;
      animation: 1s cubic-bezier(0.14, 0.93, 0.6, 1.01) 0s 1 slideInBottom;

      a {
        text-decoration: none;
        color: inherit;
        transition: all .13s ease;
        
        &:hover {
        transform: scale(1.1);

      }
      }
    }
  }
}
</style>