<script setup></script>

<template>
  <section id="home">
    <img src="/tristan-carter.jpeg" alt="" />
    <div id="home-details">
      <h1>Hi, I'm Tristan Carter.</h1>
      <h2>I am a <span>web developer</span></h2>
      <p>
        Lorem ipsum dolor sit amet consectetur, adipisicing elit. Ad nisi distinctio aspernatur quia
        velit consequuntur assumenda sint, facilis neque illo incidunt quasi laudantium temporibus
        porro.
      </p>
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Non, doloribus. Molestias cum
        quibusdam numquam quae?
      </p>
    </div>
  </section>
</template>

<style scoped>
#home {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: flex-start;
  gap: var(--lg-gap);
  img {
    aspect-ratio: 1/1;
    width: 35%;
    border-radius: 50%;
    box-shadow: var(--primary-shadow3);
  }
  #home-details {
    display: flex;
    flex-direction: column;

    h1 {
      font-size: 42px;
      margin-bottom: var(--md-gap);
    }
    h2 {
      text-align: left;
      color: var(--text-color);
      span {
        color: var(--primary);
        font-family: var(--header-font);
      }
    }
    p {
      line-height: var(--lh2);
      margin-bottom: var(--sm-gap);
    }
  }
}
</style>
