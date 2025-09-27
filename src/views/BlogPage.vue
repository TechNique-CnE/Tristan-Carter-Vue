<script setup>
import { RouterLink } from 'vue-router'
import postsData from '@/assets/blogPosts.json'
</script>

<template>
  <main>
    <section id="blog">
      <h2>This is the blog page</h2>
      <ul>
        <li v-for="post in postsData.blogPosts" :key="post.id">
          <div v-if="post.featured">
            <p>{{ post.title }}</p>
            <p>{{ post.about }}</p>
            <router-link class="int-link" :to="{ name: 'post', params: { link: post.link } }">
              Read More...
            </router-link>
          </div>
        </li>
      </ul>
    </section>
  </main>
</template>

<style scoped>
#blog {
  background-color: var(--bg);
  ul {
    list-style-type: none;
    display: flex;
    flex-direction: column;
    gap: var(--lg-gap);

    li {
      border: var(--border);
      border-radius: 10px;
      padding: var(--md-gap);

      p:nth-child(1) {
        margin-bottom: var(--sm-gap);
        font-size: var(--fs-md);
        color: var(--secondary);
      }
      p:nth-child(2) {
        text-indent: 2rem;
        line-height: var(--lh2);
      }
      a.int-link {
        color: var(--secondary);
        display: block;
        width: fit-content;
        margin: 0 var(--md-gap) 0 auto;
      }
    }
  }
}
</style>
