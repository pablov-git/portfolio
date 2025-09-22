<script setup>
import { defineEmits } from 'vue'

defineProps({
  isOpen: Boolean
})
const emit = defineEmits(['close'])

function closeChat() {
  emit('close')
}
</script>


<template>
  <div v-if="isOpen" class="chat-window">
    <div class="chat-header">
      <h3>Chatbot</h3>
      <button class="close-btn" @click="closeChat">✖</button>
    </div>
    <div class="chat-body">
      <p>Prueba</p>
    </div>
    <div class="chat-footer">
      <input type="text" placeholder="Escribe un mensaje" />
      <button class="send-btn">Enviar</button>
    </div>
  </div>
</template>

<style scoped>
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
  overflow-y: auto;
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
