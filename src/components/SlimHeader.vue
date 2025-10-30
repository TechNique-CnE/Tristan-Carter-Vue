<script setup>
import { RouterLink } from 'vue-router'
import AnimatedText from './animationComponents/AnimatedText.vue'
import ThemeBtn from './ThemeBtn.vue'
</script>

<template>
  <header>
    <!-- logo -->
    <div class="container">
      <router-link to="/"><img src="/public/tc-logo.PNG" alt="Tristan Carter Logo" /></router-link>
      <nav>
        <!-- links -->
        <router-link class="nav-link" to="/projects">
          <AnimatedText>Projects</AnimatedText>
        </router-link>
        <!-- <router-link class="nav-link" to="/blog">
          <AnimatedText>Blog</AnimatedText>
        </router-link> -->
        <router-link class="nav-link" to="/contact">
          <AnimatedText>Contact</AnimatedText>
        </router-link>
        <router-link class="nav-link" to="/about">
          <AnimatedText>About</AnimatedText>
        </router-link>
        <ThemeBtn />
      </nav>
    </div>
  </header>
</template>

<style scoped>
header {
  width: 100%;
  background-color: var(--bg2);
  padding: var(--sm-gap);
  backdrop-filter: blur(10px);
  border-bottom: var(--border);
  z-index: 10;
  margin-bottom: 60px;

  .container {
    width: var(--content-width);
    margin: 0 auto;
    display: flex;
    align-items: flex-end;
    justify-content: flex-start;
    gap: var(--md-gap);

    a img {
      width: 75px;
      aspect-ratio: 3/2;
      transition: var(--transition);
    }
    a img:hover {
      scale: 1.05;
    }

    nav {
      display: flex;
      flex-wrap: wrap;
      align-items: flex-end;
      justify-content: space-around;
      width: 75%;
      margin: 0 auto;

      .nav-link {
        padding: 5px 10px 0;
        margin-bottom: 10px;
        font-size: var(--fs-sm);
        list-style: none;
        color: var(--txt-color);
        text-decoration: none;
        transition: var(--transition);
        cursor: pointer;
        background-color: transparent;
        border: none;
        border: 2px solid transparent;
      }

      .nav-link:hover {
        border-bottom: 2px solid var(--primary);
        color: var(--primary);
        scale: 1.05;
      }
    }
  }
}
</style>
