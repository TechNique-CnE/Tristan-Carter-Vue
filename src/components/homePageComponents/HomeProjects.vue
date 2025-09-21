<script setup>
import HomeProjectCard from './HomeProjectCard.vue'
import jsonData from '../../assets/projects.json'
const projectData = jsonData.projects
import { ref, computed } from 'vue'

const currentIndex = ref(0)
const cards = ref([])
const maxIndex = computed(() => projectData.length - 1)

const scrollToCard = (index) => {
  animateScrollToCard(index, 600)
}

function animateScrollToCard(index, duration = 600) {
  const cardEl = cards.value[index]?.$el
  const trackEl = document.querySelector('.carousel-track')
  if (!cardEl || !trackEl) return

  const cardRect = cardEl.getBoundingClientRect()
  const trackRect = trackEl.getBoundingClientRect()

  const currentScroll = trackEl.scrollLeft
  const trackOffset = cardRect.left - trackRect.left
  const targetScroll = currentScroll + trackOffset - trackRect.width / 2 + cardRect.width / 2

  const startTime = performance.now()

  function animate(time) {
    const elapsed = time - startTime
    const progress = Math.min(elapsed / duration, 1)
    // Ease in-out cubic
    const ease =
      progress < 0.5 ? 4 * progress * progress * progress : 1 - Math.pow(-2 * progress + 2, 3) / 2
    trackEl.scrollLeft = currentScroll + (targetScroll - currentScroll) * ease
    if (progress < 1) {
      requestAnimationFrame(animate)
    }
  }

  requestAnimationFrame(animate)
}

const previousSlide = () => {
  currentIndex.value = currentIndex.value > 0 ? currentIndex.value - 1 : maxIndex.value
  scrollToCard(currentIndex.value)
}

const nextSlide = () => {
  currentIndex.value = currentIndex.value < maxIndex.value ? currentIndex.value + 1 : 0
  scrollToCard(currentIndex.value)
}
</script>

<template>
  <section id="home-projects">
    <h2>Featured Projects</h2>
    <div class="carousel-container">
      <button type="button" @click="previousSlide">L</button>
      <div class="carousel-track">
        <div class="carousel">
          <HomeProjectCard
            v-for="(items, index) in projectData"
            :key="items.id"
            :ref="(el) => (cards[index] = el)"
            :id="items.id"
            :title="items.title"
            :image="items.image"
            :smallDesc="items.smallDesc"
            :about="items.about"
            :link1="items.link1"
            :link2="items.link2"
          ></HomeProjectCard>
        </div>
      </div>
      <button type="button" @click="nextSlide">R</button>
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
      cursor: pointer;
      transition: var(--transition);
    }
    button:hover {
      scale: 1.05;
      box-shadow: var(--primary-shadow);
    }
    button:disabled {
      color: var(--primary2);
      box-shadow: none;
      scale: none;
      border-color: var(--primary2);
      cursor: not-allowed;
    }
    .carousel-track {
      overflow-x: auto;
      padding: 0 20%;
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

      .carousel {
        width: max-content;
        display: flex;
        flex-direction: row;
        flex-wrap: nowrap;
        gap: var(--xl-gap);
        scroll-snap-type: x mandatory;
      }
    }
    .carousel-track::-webkit-scrollbar {
      display: none;
    }
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
