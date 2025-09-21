<script setup>
import { ref } from 'vue'
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import { faHeadset } from '@fortawesome/free-solid-svg-icons'

const isChatOpen = ref(false)

function toggleChat() {
  isChatOpen.value = !isChatOpen.value
}
</script>

<template>
  <!-- Botón flotante -->
  <button class="headset-button" @click="toggleChat">
    <FontAwesomeIcon class="headset-icon" :icon="faHeadset" />
  </button>

  <!-- Ventana del chatbot -->
  <div v-if="isChatOpen" class="chat-window">
    <div class="chat-header">
      <h3>Chatbot</h3>
      <button class="close-btn" @click="toggleChat">✖</button>
    </div>
    <div class="chat-body">
      <p>Prueba</p>
    </div>
    <div class="chat-footer">
      <input type="text" placeholder="Escribe un mensaje..." />
      <button>Enviar</button>
    </div>
  </div>
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

.chat-window {
  position: fixed;
  bottom: 130px;
  right: 40px;
  width: 320px;
  height: 420px;
  background: #fff;
  border-radius: 16px;
  box-shadow: 0 6px 12px rgba(0,0,0,0.3);
  display: flex;
  flex-direction: column;
  overflow: hidden;
  z-index: 1000;
}

.chat-header {
  background: var(--sky);
  color: var(--floral-white);
  padding: 10px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.chat-header h3 {
  margin: 0;
  padding: 10px;
  font-size: 1.4rem;
}

.chat-body {
  flex: 1;
  padding: 10px;
  overflow-y: auto; /* Scroll vertical */
}

.chat-body p {
  color: var(--eerie-black);
}

.chat-footer {
  display: flex;
  padding: 10px;
  border-top: 2px solid #ccc;
}

.chat-footer input {
  flex: 1;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 8px;
  font: inherit;
}

.chat-footer button {
  margin-left: 8px;
  padding: 8px 12px;
  border: none;
  border-radius: 8px;
  background: var(--sky);
  color: var(--floral-white);
  cursor: pointer;
  font: inherit;
  font-weight: bold;
}

.close-btn {
  background: none;
  border: none;
  padding: 10px;
  color: var(--floral-white);
  font-size: 18px;
  cursor: pointer;
}
</style>
