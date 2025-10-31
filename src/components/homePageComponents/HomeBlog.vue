<script setup>
import jsonData from '../../assets/blogPosts.json'
const blogPosts = jsonData.blogPosts
// seperated by software, hardware, gaming, general
</script>

<template>
  <section id="home-blog">
    <h2>Most Recent Blog Posts</h2>
    <!-- Need to add a function to only grab the 3 most recent blog posts -->
    <ul>
      <li v-for="(blogPost, index) in blogPosts" :key="index.id">
        <p>{{ blogPost.title }}</p>
        <p>{{ blogPost.about }}</p>
        <router-link class="int-link" :to="{ name: 'post', params: { link: blogPost.link } }">
          Read More...
        </router-link>
      </li>
    </ul>

    <router-link class="int-link" to="/blog">All Blog Posts -></router-link>
  </section>
</template>

<style scoped>
#home-blog {
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
  a.int-link {
    color: var(--primary);
    display: block;
    width: fit-content;
    margin: var(--md-gap) var(--md-gap) 0 auto;
  }
}
</style>
