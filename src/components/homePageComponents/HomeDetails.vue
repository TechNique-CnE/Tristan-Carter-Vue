<script setup></script>

<template>
  <section id="home">
    <img src="/tristan-carter.jpeg" alt="" />
    <div id="home-details">
      <h1>Hi, I'm Tristan<span> Carter.</span></h1>
      <h2>I am a <span id="change-text-animation">web developer.</span></h2>
      <p>
        I enjoy producing customized solutions that extend the capabilities of small-medium
        businesses.
      </p>
      <p>
        I am passionate about contributing clean, accessible, and responsive code while delivering
        fully functional and beautiful products to clients.
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
  background-color: var(--bg);
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
      span {
        color: var(--primary);
        font-family: var(--header-font);
      }
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
      margin-bottom: var(--md-gap);
    }
  }
}
</style>
