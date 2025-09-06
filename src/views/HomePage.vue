<script setup></script>

<template>
  <main>
    <!-- ---------------- Home --------------------- -->
    <section id="home">
      <img src="/tristan-carter.jpeg" alt="" />
      <div id="home-details">
        <h1>Hey, I'm Tristan Carter.</h1>
        <h2>I am a <span>web developer</span></h2>
        <p>
          Lorem ipsum dolor sit amet consectetur, adipisicing elit. Ad nisi distinctio aspernatur
          quia velit consequuntur assumenda sint, facilis neque illo incidunt quasi laudantium
          temporibus porro.
        </p>
        <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Non, doloribus. Molestias cum
          quibusdam numquam quae?
        </p>
      </div>
    </section>
    <!-- ------------------- Projects --------------- -->
    <section id="home-projects">
      <h2>Some Projects</h2>
      <div id="projects-card-container">
        <div class="project-card"><h3>Project 1</h3></div>
        <div class="project-card"><h3>Project 2</h3></div>
        <div class="project-card"><h3>Project 3</h3></div>
      </div>
    </section>
  </main>
</template>

<style scoped>
@import '../assets/base.css';
main {
  width: 100%;
}

#home {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: flex-start;
  width: var(--content-width);
  margin: var(--md-gap) auto;
  gap: var(--lg-gap);
  img {
    aspect-ratio: 1/1;
    height: 70dvh;
    border-radius: 50%;
  }
  #home-details {
    display: flex;
    flex-direction: column;

    h1 {
      font-size: 42px;
      margin-bottom: var(--lg-gap);
    }
    h2 {
      margin-bottom: var(--md-gap);
      span {
        color: var(--primary);
      }
    }
    p {
      line-height: var(--lh2);
      margin-bottom: var(--sm-gap);
    }
  }
}

#home-projects {
  background-color: var(--bg2);
  width: var(--content-width);
  margin: var(--md-gap) auto;
}
</style>
