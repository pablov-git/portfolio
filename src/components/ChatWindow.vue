<script setup>
import { defineEmits, ref, nextTick } from 'vue'
import ChatMessage from './ChatMessage.vue'

defineProps({
  isOpen: Boolean
})
const emit = defineEmits(['close'])

function closeChat() {
  emit('close')
}

const inputText = ref('')
const chatBody = ref(null)
function sendMessage() {
  if (!inputText.value.trim()) return;
  const userMessage = { sender: 'user', message: inputText.value }
  messageList.value.push(userMessage)
  inputText.value = ''

  nextTick(() => {
    if (chatBody.value) {
      chatBody.value.scrollTo({
        top: chatBody.value.scrollHeight,
        behavior: 'smooth'
      })
    }
  })
}


const messageList = ref([
  {
    sender: 'bot',
    message: 'Hello, how can I help you?'
  }
])
</script>

<template>
  <div v-if="isOpen" class="chat-window">
    <div class="chat-header">
      <h3>Chatbot</h3>
      <button class="close-btn" @click="closeChat">✖</button>
    </div>

    <div class="chat-body" ref="chatBody">
      <ChatMessage
        :class="message.sender == 'user' ? 'message-right' : 'message-left'"
        v-for="message in messageList"
        :sender="message.sender"
        :message="message.message"
        :key="message.message"
      />
    </div>

    <div class="chat-footer">
      <input
        @keyup.enter="sendMessage"
        v-model="inputText"
        class="imput-field"
        type="text"
        placeholder="Escribe un mensaje"
      />
      <button @click="sendMessage" class="send-btn">Enviar</button>
    </div>
  </div>
</template>

<style scoped>
.message-right {
  width: 70%;
  margin-left: auto;
}

.message-left {
  width: 70%;
  margin-right: auto;
}

.chat-window {
  position: fixed;
  bottom: 130px;
  right: 40px;
  width: 320px;
  height: 420px;
  background: #fff;
  border-radius: 16px;
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.3);
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
  overflow-x: hidden;
  display: flex;
  flex-direction: column;
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
