<script setup></script>

<template>
  <section>
    <div class="about-container">
      <img src="/public/tristan-carter.jpeg" alt="a dev" />

      <div class="details">
        <h2>About Me</h2>
        <p>
          I am a freelance full-stack web developer that loves building smooth, responsive,
          user-focused experiences with Nuxt. I enjoy turning ideas into performant, accessible
          websites and apps with an intuitive design. I am always learning and expanding my skills,
          from full-stack development to experimenting with the Unity game engine and even hands-on
          PC hardware upgrades. Whether it's a business site, a personal project, or something
          experimental, I bring a genuine passion for building projects that are polished,
          puposeful, and built to last.
        </p>
      </div>
    </div>
  </section>
</template>

<style scoped>
section {
  min-height: auto;
  background-color: var(--bg);
  div.about-container {
    display: flex;
    flex-direction: row;
    justify-content: center;
    gap: var(--lg-gap);
    img {
      align-self: center;
      width: clamp(300px, 30%, 500px);
      aspect-ratio: 1/1;
      border-radius: 15px;
    }
    div.details {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      text-align: center;
      line-height: var(--lh2);
      h2{
        padding-bottom: var(--md-gap);
      }
    }
  }
}

@media screen and (max-width: 940px) {
  section {
    div.about-container {
      flex-direction: column;
      justify-content: center;
      align-items: center;
      img {
        width: 50vw;
      }
    }
  }
}
</style>
