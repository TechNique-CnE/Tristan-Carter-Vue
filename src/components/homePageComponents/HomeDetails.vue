<script setup>
import SocialLinks from '../SocialLinks.vue';
</script>

<template>
  <section id="home">
    <img src="/tristan-carter.jpeg" alt="" />
    <div id="home-details">
      <h1>Hi, I'm Tristan<span> Carter.</span></h1>
      <h2>I am a <span id="change-text-animation">web developer.</span></h2>
      <p>
        I build custom solutions for small-medium businesses to help them grow their online presence.
      </p>
      <p>
        I provide everything from consulting to full-stack development, from advice to complete apps.
      </p>
      <div class="social-links">
        <SocialLinks />
        <router-link to="/contact" class="contact-btn">Contact Me!</router-link>
      </div>
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
    width: clamp(300px, 30vw, 450px);
    border-radius: 50%;
    box-shadow: var(--primary-shadow3);
  }
  #home-details {
    display: flex;
    flex-direction: column;

    h1 {
      font-size: 42px;
      span {
        color: var(--primary);
        font-family: var(--header-font);
      }
    }
    h2 {
      text-align: left;
      color: var(--text-color);
      padding-bottom: var(--sm-gap);
      span {
        color: var(--primary);
        font-family: var(--header-font);
      }
    }
    p:first-of-type {
      padding-bottom: 5px;
    }
    p {
      padding-left: var(--sm-gap);
      line-height: var(--lh2);
    }
  }
}
.social-links {
  display: flex;
  flex-direction: column;
  gap: var(--md-gap);

  .contact-btn {
    height: 50px;
    width: 150px;
    color: black;
    border: var(--border);
    border-radius: 25px;
    transition: ease-out 350ms;
    background-color: var(--primary);
    display: flex;
    justify-content: center;
    align-items: center;
    text-decoration: none;
    font-weight: bold;
  }
  .contact-btn:hover {
    scale: 1.1;
    box-shadow: var(--primary-shadow);
    transition: var(--transition);
  }
}
@media screen and (max-width: 1000px) {
  #home {
    #home-details {
      h1 {
        font-size: var(--fs-lg);
      }
      h2 {
        font-size: var(--fs-md);
      }
    }
  }
}
@media screen and (max-width: 900px) {
  #home {
    flex-direction: column;
  }
}

</style>
