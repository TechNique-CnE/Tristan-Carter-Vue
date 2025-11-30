<template>
<div class="services-container">
  <div class="service-card">
    <h3>Web Design</h3>
    <p>Taking an idea or napkin sketch and designing a clean, modern, website out of it.</p>
  </div>
  <div class="service-card">
    <h3>Full-Stack Development</h3>
    <p>
      Lorem ipsum dolor, sit amet consectetur adipisicing elit. Ad molestias placeat deleniti,
      nostrum itaque quas, praesentium numquam quia sit temporibus quos perspiciatis ipsam,
      consequatur vero minus esse officiis! Eos, esse.
    </p>
  </div>
  <div class="service-card">
    <h3>SEO</h3>
    <p>
      Lorem ipsum dolor sit, amet consectetur adipisicing elit. Iure voluptas totam ipsum
      accusamus dignissimos explaining the service.
    </p>
  </div>
  <div class="service-card">
    <h3>This is a service</h3>
    <p>
      Lorem ipsum dolor sit, amet consectetur adipisicing elit. Iure voluptas Lorem ipsum dolor
      sit amet. totam ipsum accusamus dignissimos magnam explaining the service.
    </p>
  </div>
</div>
</template>

<style scoped>
.services-container {
  display: grid;
  grid-template-columns: 2fr 2fr;
  grid-template-rows: 1fr 1fr;
  gap: var(--lg-gap);
}

.service-card {
  padding: var(--sm-gap);
  border: 2px solid var(--accent);
  border-radius: 15px;
  transition:
    border var(--transition),
    scale var(--transition);

  h3 {
    padding-bottom: var(--sm-gap);
    text-align: center;
    transition: var(--transition);
  }

  p {
    padding: 0 var(--md-gap);
  }
}

.service-card:hover {
  border: var(--border);
  scale: 1.05;

  h3 {
    color: var(--primary);
  }
}

.service-card:nth-child(1) {
  transform-origin: left top;
}
.service-card:nth-child(2) {
  transform-origin: right top;
}
.service-card:nth-child(3) {
  transform-origin: left bottom;
}
.service-card:nth-child(4) {
  transform-origin: right bottom;
}

@media screen and (max-width: 850px) {
  .services-container {
  display: flex;
  flex-direction: column;
  gap: var(--lg-gap);
  text-align: left;
}
  .service-card {

    h3 {
      padding: 0 var(--sm-gap);
      padding-bottom: var(--sm-gap);
      text-align: left;
    }

    p {
    text-align: left;
  }
  }
  .service-card:nth-child(1),
  .service-card:nth-child(2),
  .service-card:nth-child(3),
  .service-card:nth-child(4) {
  transform-origin: center bottom;
}
}
</style>
