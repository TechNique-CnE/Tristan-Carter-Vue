<script setup>
import { BiLogoGithub, BiLogoInstagramAlt, BiLogoMeta, BiLogoLinkedinSquare } from 'vue-icons-plus/bi';
</script>

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
      <div class="social-links">
        <div class="links">
          <a href="https://www.linkedin.com/in/tristan27/" target="_blank">
            <BiLogoLinkedinSquare />
          </a>
          <a href="https://github.com/Tristan2772" target="_blank">
            <BiLogoGithub />
          </a>
          <a href="https://www.instagram.com/technique.cne/" target="_blank">
            <BiLogoInstagramAlt />
          </a>
          <a href="https://www.facebook.com/TechNique.CnE/" target="_blank">
            <BiLogoMeta />
          </a>
        </div>
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

  .links {
    padding-top: var(--md-gap);
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    align-items: center;
    gap: var(--md-gap);

    a {
      width: 50px;
      aspect-ratio: 1/1;
      border: var(--border);
      border-radius: 50%;
      transition: ease-out 350ms;
      display: flex;
      align-items: center;
      justify-content: center;
      color: var(--primary);
    }
    a:hover {
      scale: 1.1;
      color: black;
      background-color: var(--primary);
      box-shadow: var(--primary-shadow);
      transition: var(--transition);
    }
  }
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
