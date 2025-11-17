<script setup>
import jsonData from '../../assets/projects.json'
const projectData = jsonData.projects
const softwareProjectData = projectData.filter((project) => project.category == 'software')
</script>

<template>
  <section id="software-Proj">
    <h2>My Projects</h2>
    <div class="projects-container">
      <div class="project-card" v-for="projects in softwareProjectData" :key="projects.id">
        <img :src="projects.image" :alt="projects.smallDesc" />
        <div class="details">
          <h3>{{ projects.title }}</h3>
          <p>{{ projects.about }}</p>
          <div class="links">
            <a :href="projects.link1" target="_blank">Website</a>
            <a :href="projects.link2" target="_blank">Repo</a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
#software-Proj {
  background-color: var(--bg);
}
.projects-container {
  width: 100%;
  display: flex;
  flex-direction: column;
  gap: var(--lg-gap);
}

.project-card {
  text-align: left;
  display: flex;
  flex-direction: row;
  padding-left: var(--md-gap);
  background-image: linear-gradient(45deg, var(--bg), var(--bg2), var(--bg2));
  background-repeat: no-repeat;
  border-left: solid 6px var(--primary);
  border-bottom: 2px solid var(--bg);
  border-top: 2px solid var(--bg);
  border-right: 2px solid var(--bg);
  border-radius: 0 20px 20px 0;

  img {
    display: block;
    aspect-ratio: 2/1;
    width: 36%;
    margin: var(--md-gap) 0;
    border-radius: 15px;
  }
  .details {
    padding: var(--md-gap);
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    p {
      padding: var(--sm-gap) var(--sm-gap) 0;
      line-height: var(--lh2);
    }
    div.links {
      padding-bottom: var(--sm-gap);
      text-align: left;
      a {
        color: var(--primary);
      }
      a:nth-child(2) {
        padding-left: var(--sm-gap);
        color: var(--secondary);
      }
    }
  }
}
.project-card:nth-child(even) {
  text-align: right;
  flex-direction: row-reverse;
  padding-right: var(--md-gap);
  border-left: solid 2px var(--bg);
  border-right: solid 6px var(--primary);
  border-radius: 20px 0 0 20px;
  background-image: linear-gradient(135deg, var(--bg2), var(--bg2), var(--bg));

  .details div.links {
    text-align: right;
  }
}
</style>
