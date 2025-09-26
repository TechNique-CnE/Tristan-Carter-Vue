<script setup>
import { RouterLink } from 'vue-router'
import postsData from '@/assets/blogPosts.json'
</script>

<template>
  <main>
    <section>
      <h2>This is the blog page</h2>
      <ul>
        <li v-for="post in postsData.blogPosts" :key="post.id">
          <div v-if="post.featured">
            <h3>{{ post.title }}</h3>
            <p>{{ post.about }}</p>
            <router-link :to="{ name: 'post', params: { link: post.link } }">
              View Here!
            </router-link>
          </div>
        </li>
      </ul>
    </section>
  </main>
</template>
