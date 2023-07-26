<script setup>
import { RouterLink } from 'vue-router';
</script>

<template>
  <header>
    <nav class="container">
      <div class="branding">
        <h1>Awful Task Manager</h1>
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
  background-color: #212121;
  nav {
    display: flex;
    align-items: center;
    padding: 25px 16px;

    .branding {
      display: flex;
      align-items: center;

      h1 {
        font-size: 24px;
        color: white;
      }
    }

    .nav-routes {
      display: flex;
      flex: 1;
      justify-content: flex-end;
      align-items: center;
      gap: 12px;
      list-style: none;
      color: white;

      a {
        text-decoration: none;
        color: inherit;
      }
    }
  }
}
</style>