<script setup>
import { ref } from 'vue'
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import { faHeadset } from '@fortawesome/free-solid-svg-icons'
import ChatWindow from './ChatWindow.vue'

const isChatOpen = ref(false)

function toggleChat() {
  isChatOpen.value = !isChatOpen.value
}
</script>

<template>
  <button class="headset-button" @click="toggleChat">
    <FontAwesomeIcon class="headset-icon" :icon="faHeadset" />
  </button>

  <ChatWindow :isOpen="isChatOpen" @close="isChatOpen = false" />
</template>

<style scoped>
.headset-button {
  position: fixed;
  bottom: 40px;
  right: 40px;
  border-radius: 50%;
  padding: 10px;
  font-size: 20px;
  background-color: var(--sky);
  border: none;
  cursor: pointer;
  width: 75px;
  height: 75px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  transition: transform 0.2s ease;
  z-index: 1001;
}

.headset-button:hover {
  transform: scale(1.10);
}

.headset-icon {
  color: var(--floral-white);
  width: 50px;
  height: 50px;
}
</style>
