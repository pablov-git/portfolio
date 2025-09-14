<script setup>
defineProps({
  title: String,
  image: String,
  technologies: Array,
})
</script>

<template>
  <div class="project_card">
    <h3 class="project_title">{{ title }}</h3>
    <img :src="image" :alt="title" class="project_image" />
    <div class="project_technologies">
      <span v-for="tech in technologies" :key="tech" class="tech_name">{{ tech }}</span>
    </div>
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
  min-height: 300px;
}

.project_card:hover {
  transform: translateY(-5px) scale(1.03);
  box-shadow: 0 0 25px var(--sky);
}

.project_image {
  width: 100%;
  border-radius: 0.5rem;
  margin-bottom: 1rem;
  object-fit: cover;
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
}

.tech_name {
  background: var(--timberwolf);
  color: var(--eerie-black);
  padding: 0.3rem 0.6rem;
  border-radius: 0.4rem;
  font-size: 0.9rem;
  font-weight: 600;
}
</style>
