<script setup>
import HomeProjectCard from './HomeProjectCard.vue'
import jsonData from '../assets/projects.json'
const projectData = jsonData.projects
</script>

<template>
  <section id="home-projects">
    <h2>Featured Projects</h2>
    <div id="home-projects-container">
      <HomeProjectCard
        v-for="(items, index) in projectData"
        :key="items"
        :id="projectData[index].id"
        :title="projectData[index].title"
        :image="projectData[index].image"
        :smallDesc="projectData[index].smallDesc"
        :about="projectData[index].about"
        :link1="projectData[index].link1"
        :link2="projectData[index].link2"
      ></HomeProjectCard>
    </div>
    <router-link to="/projects">See All Projects -></router-link>
  </section>
</template>

<style scoped>
#home-projects {
  background-color: var(--bg2);
  width: var(--content-width);
  margin: var(--md-gap) auto;

  h2 {
    text-align: center;
    padding-bottom: var(--md-gap);
  }

  #home-projects-container {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    gap: var(--md-gap);
  }
}
</style>
