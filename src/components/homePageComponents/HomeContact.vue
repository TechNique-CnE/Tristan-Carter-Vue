<script setup></script>

<template>
  <section id="home-contact">
    <div>
      <h2>Contact Me!</h2>
      <p>
        If you have any questions, please refer to the <router-link to="/faq">faq</router-link>. If you don't
        see an answer for your question, feel free to ask in the
        <router-link to="/contact">form</router-link> or simply <a href="mailto:tristancarter2772@gmail.com">email me</a>.
      </p>
    </div>
  </section>
</template>

<style scoped>
section#home-contact {
  margin-top: 80px;
  min-height: 25%;
  background-image: linear-gradient(
    135deg,
    var(--secondary),
    var(--primary),
    var(--secondary),
    var(--secondary),
    var(--secondary)
  );
  border: var(--border);
  color: black;
  text-align: center;
  div {
    margin: auto 0;
    h2 {
      color: black;
      padding-bottom: var(--md-gap);
    }
    p {
      line-height: var(--lh2);
      font-size: var(--fs-sm);
      a {
        color: black;
      }
    }
  }
}
</style>
