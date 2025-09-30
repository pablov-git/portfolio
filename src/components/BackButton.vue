<script setup>
import { RouterLink } from 'vue-router'
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import { faArrowLeft } from '@fortawesome/free-solid-svg-icons'

defineProps({
  to: { type: String, default: '/' }
})
</script>

<template>
  <RouterLink :to="to" class="back-arrow">
    <FontAwesomeIcon :icon="faArrowLeft" class="arrow-icon" />
  </RouterLink>
</template>

<style scoped>
.back-arrow {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  text-decoration: none;
  font-weight: 700;
  font-size: 1.25rem;
  color: var(--sky);
  transition: color 0.2s, transform 0.2s;
}

.back-arrow:hover {
  color: var(--floral-white);
  transform: translateX(-3px);
}

.arrow-icon {
  font-size: 1.8rem;
}

.back-label {
  font-weight: 700;
  font-size: 1.25rem;
}
</style>
