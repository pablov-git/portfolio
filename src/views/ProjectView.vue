<script setup>
import ProjectCard from '../components/ProjectCard.vue'

const projects = [
  {
    title: 'E-Commerce',
    image: '/thumbnails/proyectoEcommerce.png',
    technologies: ["JavaScript", "HTML5", "CSS3"],
    link: 'https://github.com/pablov-git/e-commerce'
  },
  {
    title: 'Filmoteca',
    image: '/thumbnails/proyectoPeliculas.png',
    technologies: ["Vue.js"],
    link: 'https://github.com/pablov-git/favourite-films'
  },
  {
    title: 'To Do List',
    image: '/thumbnails/proyectoTodolist.png',
    technologies: ["JavaScript", "Bootstrap", "HTML5", "CSS3"],
    link: 'https://github.com/pablov-git/to-do-list'
  },
]

</script>

<template>
  <section class="projects">
    <h1 class="projects_title">Mis proyectos</h1>
    <div class="projects_grid">
      <ProjectCard
        v-for="project in projects"
        :key="project.title"
        :title="project.title"
        :image="project.image"
        :technologies="project.technologies"
        :link="project.link"
      />
    </div>
  </section>
</template>

<style scoped>
.projects {
  max-width: 1200px;
  margin: 4rem auto;
  padding: 0 2rem 5rem;
}

.projects_title {
  font-size: 2.5rem;
  color: var(--floral-white);
  margin-bottom: 4rem;
  text-align: center;
}

.projects_grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(450px, 1fr));
  gap: 2rem;
}
</style>
