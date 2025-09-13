<script setup>
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
  background-color: var(--bg2);
  padding: var(--sm-gap);
  backdrop-filter: blur(10px);
  z-index: 10;

  .container {
    width: var(--content-width);
    margin: 0 auto;
    display: flex;
    align-items: flex-end;
    justify-content: flex-start;
    gap: var(--md-gap);

    a img {
      height: 75px;
      aspect-ratio: 1/1;
      border-radius: 50%;
      border: 1px solid white;
      transition: var(--transition);
      box-shadow: var(--primary-shadow);
    }
    a img:hover {
      box-shadow: var(--primary-shadow2);
      scale: 1.05;
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
        margin: 0 var(--sm-gap) var(--sm-gap) 0;
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
        scale: 1.05;
      }
    }
  }
}
</style>
