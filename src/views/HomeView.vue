<script setup>
import profilePhotoColor from '../../public/profilePhotoColor.png'
import TechCard from '../components/TechCard.vue'

const technologies = [
  { name: 'Vue.js', logo: '/logos/vue.png', level: 2 },
  { name: 'JavaScript', logo: '/logos/javascript.png', level: 3 },
  { name: 'HTML5', logo: '/logos/html.png', level: 4 },
  { name: 'CSS3', logo: '/logos/css.png', level: 4 },
  { name: 'Bootstrap', logo: '/logos/bootstrap.png', level: 4 },
  { name: 'Java', logo: '/logos/java.png', level: 2 },
  { name: 'SQL', logo: '/logos/sql.png', level: 2 },
  { name: 'Git', logo: '/logos/git.png', level: 3 }
]
</script>

<template>
  <section class="intro">
    <div class="container">
      <!-- Texto -->
      <div class="intro_text">
        <h1 class="intro_title">Hola, soy <span class="highlight">Pablo</span></h1>
        <h2 class="intro_subtitle">Desarrollador Frontend</h2>
        <p class="intro_description">
          Estoy ubicado en Madrid y me apasiona el <span class="highlight">desarrollo web</span>. Me
          especializo en crear interfaces <span class="highlight">modernas</span>,
          <span class="highlight">rápidas</span> y <span class="highlight">accesibles</span>. Siempre
          estoy abierto a <span class="highlight">nuevos proyectos</span>, así que si tienes una idea,
          no dudes en contactarme
        </p>

        <div class="intro_actions">
          <RouterLink to="/projects" class="btn btn--primary">Ver proyectos</RouterLink>
          <RouterLink to="/contact" class="btn btn--secondary">Contacto</RouterLink>
          <a href="/cv/Pablo_CV.pdf" download class="btn btn--tertiary">Descargar CV</a>
        </div>
      </div>

      <!-- Foto -->
      <div class="intro_image">
        <img class="profile-photo" :src="profilePhotoColor" alt="Foto" />
      </div>
    </div>
  </section>

  <!-- Tecnologías -->
  <section class="technologies">
    <div class="tech_row">
      <TechCard
        v-for="tech in technologies.slice(0,4)"
        :key="tech.name"
        :name="tech.name"
        :logo="tech.logo"
        :level="tech.level"
      />
    </div>
    <div class="tech_row">
      <TechCard
        v-for="tech in technologies.slice(4)"
        :key="tech.name"
        :name="tech.name"
        :logo="tech.logo"
        :level="tech.level"
      />
    </div>
  </section>
</template>

<style scoped>
/* CONTENEDORES */
.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1200px;
  margin: 4rem auto;
  gap: 8rem;
}

.intro_text {
  flex: 2;
}

.intro_image {
  flex: 1;
  display: flex;
  justify-content: center;
}

/* FOTO */
.profile-photo {
  width: 325px;
  border-radius: 50%;
  border: 6px solid var(--timberwolf);
  transition: box-shadow 0.4s ease;
}

.profile-photo:hover {
  box-shadow: 0 0 25px var(--sky);
}

/* TEXTO */
.intro_title {
  font-size: 3.5rem;
  font-weight: bold;
  margin-bottom: 1rem;
  color: var(--floral-white);
}

.intro_subtitle {
  font-size: 1.8rem;
  color: var(--sky);
  margin-bottom: 1rem;
}

.intro_description {
  font-size: 1.3rem;
  color: var(--timberwolf);
  margin-bottom: 2rem;
}

.highlight {
  color: var(--sky);
  font-weight: bold;
}

/* BOTONES CENTRADOS */
.intro_actions {
  display: flex;
  justify-content: center;
  gap: 1rem;
  flex-wrap: wrap;
}

/* BOTONES */
.btn {
  padding: 0.85rem 1.6rem;
  font-size: 1rem;
  border-radius: 2rem;
  font-weight: bold;
  text-decoration: none;
  transition: all 0.3s ease;
  display: inline-block;
}

.btn--primary {
  background: var(--sky);
  color: var(--floral-white);
  border: none;
}

.btn--primary:hover {
  background: var(--sky);
  filter: brightness(1.1);
}

.btn--secondary {
  border: 2px solid var(--sky);
  color: var(--sky);
  background: transparent;
}

.btn--secondary:hover {
  background: var(--sky);
  color: var(--floral-white);
}

.btn--tertiary {
  background: var(--timberwolf);
  color: var(--eerie-black);
  border: none;
}

.btn--tertiary:hover {
  background: var(--sky);
  color: var(--floral-white);
}

/* TECNOLOGÍAS */
.technologies {
  background: var(--rich-black);
  padding: 3.5rem 2rem;
  text-align: center;
}

.tech_row {
  display: flex;
  justify-content: center;
  gap: 1.5rem;
  margin-bottom: 1.5rem;
}
</style>
