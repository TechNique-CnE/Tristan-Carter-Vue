<script setup>
import HomeProjectCard from './HomeProjectCard.vue'
import jsonData from '../../assets/projects.json'
const projectData = jsonData.projects
import { useTemplateRef } from 'vue'

const track = useTemplateRef('track')
const scrollAmount = 3

const previousSlide = () => {
  console.log(track.value.scrollLeft)
  console.log(track.value.scrollWidth)
  // console.log(track.value.scrollBy(scrollAmount))
  if (track.value) {
    track.value.scrollBy({
      left: -scrollAmount,
      behavior: 'smooth',
    })
  }
}

const nextSlide = () => {
  if (track.value) {
    track.value.scrollBy({
      left: scrollAmount,
      behavior: 'smooth',
    })
  }
}
</script>

<template>
  <section id="home-projects">
    <h2>Featured Projects</h2>
    <div class="carousel-container">
      <button @click="previousSlide">L</button>
      <div id="home-projects-container" ref="track">
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
      <button @click="nextSlide">R</button>
    </div>
    <router-link to="/projects" class="int-link">See All Projects -></router-link>
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
  .carousel-container {
    display: flex;
    flex-direction: row;
    align-items: center;

    button {
      min-width: 50px;
      height: 50px;
      border-radius: 50%;
      border: var(--border);
      background-color: transparent;
      color: var(--primary);
      font-weight: bold;
    }
    #home-projects-container {
      display: flex;
      flex-direction: row;
      flex-wrap: no-wrap;
      gap: var(--xl-gap);
      overflow-x: scroll;
      scroll-behavior: smooth;
      scroll-snap-type: x mandatory;
      scrollbar-width: none;
      -ms-overflow-style: none;
      -webkit-mask-image: linear-gradient(
        to right,
        transparent,
        black 20%,
        black 80%,
        black 20%,
        transparent
      );
      -webkit-mask-composite: destination-in;
      -webkit-mask-repeat: no-repeat;
      -webkit-mask-size: 100% 100%;

      mask-image: linear-gradient(
        to right,
        transparent,
        black 20%,
        black 80%,
        black 20%,
        transparent
      );
      mask-repeat: no-repeat;
      mask-composite: intersect;
      mask-size: 100% 100%;
    }
    #home-projects-container::-webkit-scrollbar {
      display: none;
    }
    transition: var(--transition);
  }

  a.int-link {
    margin: var(--sm-gap) var(--md-gap) 0 auto;
    display: block;
    width: 100%;
    text-align: right;
    color: var(--primary);
  }
}
</style>
