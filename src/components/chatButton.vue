<script setup>
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import { faHeadset } from '@fortawesome/free-solid-svg-icons'
</script>

<template>
  <button class="chat-button">
    <FontAwesomeIcon class="headset-icon" :icon="faHeadset" />
  </button>
</template>

<style scoped>
.chat-button {
  position: fixed;
  bottom: 40px;
  right: 40px;
  border-radius: 50%;
  padding: 10px;
  font-size: 20px;
  background-color: var(--sky);
  border: none;
  cursor: pointer;
  width: 80px;
  height: 80px;
  box-shadow: 0 4px 8px rgba(0,0,0,0.2);
  transition: transform 0.2s ease;
}

.chat-button:hover {
  transform: scale(1.05);
}

.headset-icon {
  color: var(--floral-white);
  width: 50px;
  height: 50px;
}
</style>
