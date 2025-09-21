<script setup>
defineProps({
  title: String,
  image: String,
  technologies: Array,
  link: String
})
</script>

<template>
  <div class="project_card">
    <h3 class="project_title">{{ title }}</h3>
    <img :src="image" :alt="title" class="project_image" />
    <div class="project_technologies">
      <span v-for="tech in technologies" :key="tech" class="tech_name">{{ tech }}</span>
    </div>
    <a v-if="link" :href="link" target="_blank" rel="noopener" class="project_button">Ver proyecto</a>
  </div>
</template>

<style scoped>
.project_card {
  background: var(--eerie-black);
  border-radius: 0.8rem;
  padding: 1.5rem;
  box-shadow: 0 4px 10px rgba(0,0,0,0.4);
  display: flex;
  flex-direction: column;
  align-items: center;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.project_card:hover {
  transform: translateY(-5px) scale(1.03);
  box-shadow: 0 0 25px var(--sky);
}

.project_image {
  width: 100%;
  height: 400px;
  object-fit: cover;
  object-position: top;
  border-radius: 0.5rem;
  margin-bottom: 2rem;
  border-radius: 0.5rem;
  margin-bottom: 2rem;
}

.project_title {
  font-size: 1.5rem;
  color: var(--floral-white);
  font-weight: bold;
  margin-top: 0.5rem;
  margin-bottom: 2rem;
  text-align: center;
}

.project_technologies {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  justify-content: center;
  margin-bottom: 1.5rem;
}

.tech_name {
  background: var(--timberwolf);
  color: var(--eerie-black);
  padding: 0.3rem 0.6rem;
  border-radius: 0.4rem;
  font-size: 0.9rem;
  font-weight: 600;
}

.project_button {
  padding: 0.5rem 1rem;
  background-color: var(--sky);
  color: var(--eerie-black);
  border-radius: 0.5rem;
  text-decoration: none;
  font-weight: 600;
  transition: background-color 0.3s ease;
}

.project_button:hover {
  background-color: var(--floral-white);
}

@media (max-width: 768px) {
  .project_card {
    max-width: 420px;
    width: 100%;
    margin: 1rem auto;
    padding: 1rem;
    box-sizing: border-box;
  }

  .project_card img {
    max-height: 200px;
    margin-bottom: 1rem;
  }

  .project_card h3 {
    font-size: 1.1rem;
    margin-bottom: 1rem;
  }

  .techs span {
    font-size: 0.8rem;
    padding: 0.2rem 0.4rem;
  }

  .project_card a {
    width: 100%;
    max-width: 360px;
    text-align: center;
    padding: 0.6rem;
  }
}
</style>
