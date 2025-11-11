<script setup>
defineProps(['id', 'title', 'image', 'smallDesc', 'about', 'link1', 'link2'])
</script>

<template>
  <div class="project-card">
    <img loading="lazy" :src="image" :alt="smallDesc" />
    <h3>{{ title }}</h3>
    <p>{{ about }}</p>
    <div class="links">
      <a :href="link1" target="_blank">Website</a>
      <a :href="link2" target="_blank">Repo</a>
    </div>
  </div>
</template>

<style scoped>
.project-card {
  width: 65%;
  max-width: 480px;
  max-width: 580px;
  padding-top: var(--md-gap);
  border: 2px solid var(--primary);
  border-radius: 15px;

  h3 {
    text-align: center;
  }
  img {
    display: block;
    aspect-ratio: 2/1;
    width: 70%;
    margin: var(--md-gap) auto;
    border-radius: 15px;
  }
  p {
    text-align: center;
    padding: var(--sm-gap) var(--sm-gap);
    line-height: var(--lh2);
  }
  div.links {
    padding-right: var(--md-gap);
    padding-bottom: var(--sm-gap);
    text-align: right;
    a {
      padding-left: var(--sm-gap);
      color: var(--primary);
    }
    a:nth-child(2) {
      color: var(--secondary);
    }
  }
}
</style>
