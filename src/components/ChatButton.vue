<script setup>
import { ref } from 'vue'
import ChatWindow from './ChatWindow.vue'

const isChatOpen = ref(false)

function toggleChat() {
  isChatOpen.value = !isChatOpen.value
}
</script>

<template>
  <button class="chatbot-button" @click="toggleChat">
    <img src="/chatBotIcon.png" alt="Chatbot" class="chatbot-icon" />
  </button>

  <ChatWindow :isOpen="isChatOpen" @close="isChatOpen = false" />
</template>

<style scoped>
.chatbot-button {
  position: fixed;
  bottom: 80px;
  right: 140px;
  width: 75px;
  height: 75px;
  border-radius: 50%;
  padding: 0;
  border: none;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  background: transparent;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.6);
  transition: transform 0.3s ease, box-shadow 0.4s ease;
}

.chatbot-button:hover {
  transform: translateY(-2px) scale(1.2);
  box-shadow: 0 0 25px var(--sky);
}

.chatbot-icon {
  width: 70%;
  height: 70%;
  object-fit: contain;
}

@media (max-width: 1024px) {
  .chatbot-button {
    bottom: 30px;
    right: 30px;
    width: 65px;
    height: 65px;
  }

  .chatbot-icon {
    width: 70%;
    height: 70%;
  }
}
</style>
