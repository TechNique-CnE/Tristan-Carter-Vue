<script setup></script>

<template>
  <section id="home-contact">
    <div>
      <h2>Contact Me!</h2>
      <p>
        For contracting inquiries, please call <a href="tel:+1(405)541-6780">(405)541-6780</a>.
        Otherwise, if you have any questions, please refer to the <a href="#">FAQ</a>. If you don't
        see an answer for your question, feel free to ask in the form
        <router-link to="/contact">here</router-link>.
      </p>
    </div>
  </section>
</template>

<style scoped>
#home-contact {
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
    margin: 12% 0;
    h2 {
      color: black;
      margin-bottom: var(--md-gap);
    }
    p {
      line-height: var(--lh2);
      font-size: var(--fs-md);
      a {
        color: black;
      }
    }
  }
}
</style>
