<script setup>
import { RouterView } from 'vue-router'
import SlimHeader from './components/SlimHeader.vue'
import ThickFooter from './components/ThickFooter.vue'
</script>

<template>
  <SlimHeader />

  <RouterView />

  <ThickFooter />
</template>

<style scoped>
@import './assets/base.css';
</style>
