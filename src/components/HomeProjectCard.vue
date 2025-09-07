<script setup>
defineProps(['id', 'title', 'image', 'smallDesc', 'about', 'link1', 'link2'])
</script>

<template>
  <div class="project-card">
    <h3>{{ title }}</h3>
    <img loading="lazy" :src="image" :alt="smallDesc" />
    <p>{{ about }}</p>
    <a :href="link1">Project site</a>
    <a :href="link2">Github Repo</a>
  </div>
</template>

<style scoped>
@import '../assets/base.css';
.project-card {
  width: 45%;
  border: 2px solid var(--primary);
  padding-top: var(--md-gap);

  h3 {
    text-align: center;
  }
  img {
    display: block;
    aspect-ratio: 2/1;
    width: 80%;
    margin: var(--md-gap) auto;
  }
}
</style>
