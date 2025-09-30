<script setup>
import ProjectCard from '../components/ProjectCard.vue'
import BackButton from '../components/BackButton.vue'

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
    technologies: ["JavaScript", "HTML5", "CSS3"],
    link: 'https://github.com/pablov-git/to-do-list'
  },
  {
    title: 'Agencia de viajes',
    image: '/thumbnails/proyectoAgenciaViajes.png',
    technologies: ["JavaScript", "HTML5", "CSS3"],
    link: 'https://github.com/pablov-git/AUJ-landing-page'
  }
]

</script>

<template>
  <section class="projects">
    <BackButton to="/" />
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

/* --- MÓVIL --- */
@media (max-width: 768px) {
  .projects {
    padding: 1.5rem 1rem 3rem;
    padding-bottom: 5rem;
    margin: 2.5rem auto;
  }

  .projects_grid {
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    justify-items: center;
    gap: 1rem;
  }

  ::v-deep .project_card {
    width: clamp(300px, 92%, 420px) !important;
    margin: 0.8rem auto !important;
    align-self: center !important;
  }

  .projects_grid > * {
    justify-self: center;
    width: 100%;
    max-width: 420px;
  }
}

@media (max-width: 420px) {
  .projects_grid {
    grid-template-columns: 1fr;
    gap: 0.9rem;
  }

  .projects {
    padding: 1rem 0.75rem 2rem;
    padding-bottom: 6rem;
    margin: 1.5rem auto;
  }
}
</style>
