<script setup>
import profilePhotoColor from '../../public/profilePhotoColor.png'

const technologies = [
  { name: 'Vue.js', logo: '/logos/vue.png', level: 2 },
  { name: 'JavaScript', logo: '/logos/javascript.png', level: 3  },
  { name: 'HTML5', logo: '/logos/html.png', level: 4  },
  { name: 'CSS3', logo: '/logos/css.png', level: 4  },
  { name: 'Bootstrap', logo: '/logos/bootstrap.png', level: 4  },
  { name: 'Java', logo: '/logos/java.png', level: 2  },
  { name: 'SQL', logo: '/logos/sql.png', level: 2  },
  { name: 'Git', logo: '/logos/git.png', level: 3  },
]
</script>

<template>
  <section class="intro">
    <div class="container">
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

    <div class="intro_image">
      <img class="profile-photo" :src="profilePhotoColor" alt="Foto" />
    </div>
  </section>

  <section class="technologies">
    <div class="tech_row">
      <div v-for="tech in technologies.slice(0, 4)" :key="tech.name" class="tech_card">
        <img class="tech_logo" :src="tech.logo" :alt="tech.name" />
        <p class="tech_name">{{ tech.name }}</p>

        <div class="tech_stars" aria-hidden="true">
          <span
            v-for="n in 5"
            :key="n"
            class="star"
            :class="{ filled: n <= tech.level }"
            :style="{ '--i': n }"
          >★</span>
        </div>
      </div>
    </div>


    <div class="tech_row">
      <div v-for="tech in technologies.slice(4)" :key="tech.name" class="tech_card">
        <img class="tech_logo" :src="tech.logo" :alt="tech.name" />
        <p class="tech_name">{{ tech.name }}</p>

        <div class="tech_stars" aria-hidden="true">
          <span
            v-for="n in 5"
            :key="n"
            class="star"
            :class="{ filled: n <= tech.level }"
            :style="{ '--i': n }"
          >★</span>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.profile-photo {
  width: 325px;
  border-radius: 50%;
  border: 6px solid var(--timberwolf);
  transition: box-shadow 0.4s ease;
}

.profile-photo:hover {
  box-shadow: 0 0 25px var(--sky);
}

.intro {
  display: flex;
  align-items: center;
  justify-content: center;
  background: var(--eerie-black);
  color: var(--floral-white);
  padding: 4.5rem 2rem;
  gap: 8rem;
}

.container {
  max-width: 650px;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.intro_title {
  font-size: 2.8rem;
  font-weight: bold;
}

.intro_subtitle {
  font-size: 1.6rem;
  color: var(--sky);
  margin: 1rem 0;
}

.intro_description {
  font-size: 1.15rem;
  line-height: 1.7;
  color: var(--timberwolf);
  margin-bottom: 2rem;
}

.highlight {
  color: var(--sky);
  font-weight: bold;
}

.intro_actions {
  display: flex;
  gap: 1rem;
}

.btn {
  padding: 0.85rem 1.6rem;
  font-size: 1rem;
  border-radius: 2rem;
  font-weight: bold;
  text-decoration: none;
  transition: all 0.3s ease;
}

.btn--primary {
  background: var(--sky);
  color: var(--floral-white);
}

.btn--primary:hover {
  background: var(--sky);
}

.btn--secondary {
  border: 2px solid var(--sky);
  color: var(--sky);
}

.btn--secondary:hover {
  background: var(--sky);
  color: var(--floral-white);
}

.btn--tertiary {
  background: var(--timberwolf);
  color: var(--eerie-black);
}

.btn--tertiary:hover {
  background: var(--sky);
  color: var(--floral-white);
}

.technologies {
  background: var(--rich-black);
  padding: 3.5rem 2rem;
  text-align: center;
}

.tech_title {
  font-size: 2rem;
  margin-bottom: 2rem;
  color: var(--floral-white);
}

.tech_row {
  display: flex;
  justify-content: center;
  align-items: flex-start;
  gap: 1.5rem;
  margin-bottom: 1.5rem;
}

.tech_card {
  flex: 1;
  max-width: 130px;
  background: var(--eerie-black);
  padding: 1.2rem;
  border-radius: 0.8rem;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.4);
  display: flex;
  flex-direction: column;
  align-items: center;
  transition: box-shadow 0.4s ease, transform 0.3s ease;
  min-height: 140px;
  position: relative;
}

.tech_card:hover {
  transform: translateY(-5px) scale(1.08);
  box-shadow: 0 0 25px var(--sky);
}

.tech_logo {
  width: 60px;
  height: 60px;
  object-fit: contain;
  margin-bottom: 0.6rem;
}

.tech_name {
  font-size: 1.05rem;
  font-weight: bold;
  color: var(--timberwolf);
}

.tech_stars {
  position: absolute;
  bottom: 1rem;
  left: 50%;
  transform: translateX(-50%) translateY(5px);
  opacity: 0;
  display: flex;
  gap: 0.2rem;
  pointer-events: none;
  transition: all 0.3s ease;
}

.tech_card:hover .tech_stars {
  opacity: 1;
  transform: translateX(-50%) translateY(0);
}

.star {
  font-size: 1rem;
  color: var(--timberwolf);
  display: inline-block;
  transform: translateY(6px);
  transition:
    transform 240ms cubic-bezier(.2,.9,.2,1) calc((var(--i) - 1) * 0.04s),
    color 200ms ease calc((var(--i) - 1) * 0.04s);
}

.tech_card:hover .star {
  transform: translateY(0);
}

.star.filled {
  color: var(--sky);
}
</style>
