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
