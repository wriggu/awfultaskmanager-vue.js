<script setup>
import { RouterLink } from 'vue-router';
</script>

<template>
  <header>
    <nav class="container">
      <div class="branding">
        <h1>.ksatlufwa</h1>
      </div>    
      <ul class="nav-routes">
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </ul>
    </nav>
  </header>
</template>


<style lang="scss" scoped>
header {
  nav {
    max-width: 95%;
    display: flex;
    padding: 25px 16px;
    align-items: center;

    .branding {
      display: flex;
      align-items: center;

      h1 {
        font-size: 24px;
        color: #191815
      }
    }

    .nav-routes {
      font-weight: 500;
      margin-top: 2.5%;
      display: flex;
      flex: 1;
      justify-content: flex-end;
      gap: 12px;
      list-style: none;
      color: #191815;

      a {
        text-decoration: none;
        color: inherit;
      }
    }
  }
}
</style>