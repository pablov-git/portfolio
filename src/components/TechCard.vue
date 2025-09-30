<script setup>
defineProps({
  name: String,
  logo: String,
  level: Number
})
</script>

<template>
  <div class="tech_card">
    <img class="tech_logo" :src="logo" :alt="name" />
    <p class="tech_name">{{ name }}</p>

    <div class="tech_stars" aria-hidden="true">
      <span
        v-for="n in 5"
        :key="n"
        class="star"
        :class="{ filled: n <= level }"
        :style="{ '--i': n }"
      >★</span>
    </div>
  </div>
</template>

<style scoped>
.tech_card {
  flex: 1;
  max-width: 130px;
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.12);
  border-radius: 1rem;
  padding: 1.2rem;
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
  margin-top: 0.5rem;
  margin-bottom: 0.5rem;
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
