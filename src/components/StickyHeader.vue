<script setup>
// import { ref } from 'vue'
import { RouterLink } from 'vue-router'
</script>

<template>
  <header>
    <!-- logo -->
    <div class="container">
      <router-link to="/"><img src="/tc-logo.png" alt="Tristan Carter Logo" /></router-link>
      <nav>
        <!-- links -->
        <router-link to="/projects">Projects</router-link>
        <router-link to="/blog">Blog</router-link>
        <router-link to="/contact">Contact</router-link>
        <router-link to="/about">About</router-link>
        <button>Themes</button>
      </nav>
    </div>
  </header>
</template>

<style scoped>
@import '../assets/base.css';

header {
  width: 100%;
  background-color: var(--content-bg);
  padding: var(--md-gap);
  position: sticky;
  top: 0;
  left: 0;

  .container {
    width: var(--content-width);
    margin: 0 auto;
    display: flex;
    align-items: flex-end;
    justify-content: flex-start;
    gap: var(--md-gap);

    a img {
      width: 75px;
      height: 75px;
      border-radius: 50%;
      border: 1px solid white;
      box-shadow: 0 0 16px var(--primary);
    }

    nav {
      display: flex;
      flex-wrap: wrap;
      align-items: flex-end;
      justify-content: space-around;
      width: 75%;
      margin: 0 auto;

      a,
      button {
        font-size: var(--fs-sm);
        list-style: none;
        margin: var(--sm-gap);
        color: var(--txt-color);
        text-decoration: none;
        transition: var(--transition);
        cursor: pointer;
        background-color: transparent;
        border: none;
        border-bottom: 2px solid transparent;
      }

      a:hover,
      button:hover {
        border-bottom: 2px solid var(--primary);
        color: var(--primary);
      }
    }
  }
}
</style>
