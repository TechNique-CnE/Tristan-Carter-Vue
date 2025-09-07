<script setup>
import HomeDetails from '@/components/HomeDetails.vue'
import HomeProjects from '@/components/HomeProjects.vue'
</script>

<template>
  <main>
    <!-- ---------------- Home --------------------- -->
    <HomeDetails />
    <hr class="divider" />
    <!-- ------------------- Projects --------------- -->
    <HomeProjects />
    <hr class="divider" />
  </main>
</template>

<style scoped>
@import '../assets/base.css';
main {
  width: 100%;
}
section {
  width: var(--content-width);
  min-height: 75dvh;
  margin: var(--lg-gap) auto;
  padding: var(--md-gap) var(--lg-gap);
  backdrop-filter: blur(10px);
  border-radius: 25px;
}
</style>
