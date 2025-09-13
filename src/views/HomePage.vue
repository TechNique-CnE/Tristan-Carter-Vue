<script setup>
import HomeDetails from '@/components/homePageComponents/HomeDetails.vue'
import HomeProjects from '@/components/homePageComponents/HomeProjects.vue'
import HomeBlog from '@/components/homePageComponents/HomeBlog.vue'
</script>

<template>
  <main>
    <!-- ---------------- Home --------------------- -->
    <HomeDetails />
    <hr class="divider" />
    <!-- ------------------- Projects --------------- -->
    <HomeProjects />
    <hr class="divider" />
    <!-- ------------------- Blog -------------------- -->
    <HomeBlog />
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
  min-height: 80dvh;
  margin: var(--lg-gap) auto;
  padding: var(--md-gap) var(--lg-gap);
  backdrop-filter: blur(10px);
  border-radius: 25px;
}
</style>
