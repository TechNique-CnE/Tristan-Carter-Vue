<script setup>
import { RouterLink } from 'vue-router'
</script>

<template>
  <footer>
    <ul>
      <li><router-link to="/">home</router-link></li>
      <li><router-link to="/services">services</router-link></li>
      <li><router-link to="/projects">projects</router-link></li>
      <!-- <li><router-link to="/blog">blog</router-link></li> -->
      <li><router-link to="/contact">contact</router-link></li>
      <li><router-link to="/about">about</router-link></li>
      <li><router-link to="/faq">faq</router-link></li>
    </ul>
  </footer>
</template>

<style scoped>
footer {
  width: 100%;
  height: 50dvh;
  background-color: var(--bg2);
  backdrop-filter: blur(10px);
  padding-top: var(--lg-gap);
  margin-top: 80px;
  border-top: var(--border);

  ul {
    width: var(--content-width);
    display: flex;
    justify-content: space-around;
    flex-direction: row;
    align-items: center;
    margin: 0 auto;

    li {
      list-style-type: none;
      a {
        color: var(--text-color);
      }
    }
  }
}
</style>
