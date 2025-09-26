<script setup>
import { RouterLink } from 'vue-router'
import postsData from '@/assets/blogPosts.json'
</script>

<template>
  <main>
    <h2>This is the blog page</h2>
    <ul>
      <li v-for="post in postsData.blogPosts" :key="post.id">
        <!-- pass the filename from JSON (e.g. "blogPost1.md") as the route param -->
        <router-link :to="{ name: 'post', params: { link: post.link } }">
          {{ post.title }}
        </router-link>
      </li>
    </ul>
  </main>
</template>
