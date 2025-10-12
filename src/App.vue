<script setup>
import { RouterView } from 'vue-router'
import { ref, provide } from 'vue'
import SlimHeader from './components/SlimHeader.vue'
import ThickFooter from './components/ThickFooter.vue'
import AnimationContainer from './components/AnimationContainer.vue'

const animationClass = ref('glitch')

provide('animationClass', animationClass)
</script>

<template>
  <SlimHeader />

  <RouterView />

  <ThickFooter />
  <AnimationContainer />
</template>

<style scoped>
@import './assets/base.css';
</style>
