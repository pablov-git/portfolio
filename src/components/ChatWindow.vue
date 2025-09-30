<script setup>
import { defineEmits, ref, nextTick, watch, onMounted } from 'vue'
import ChatMessage from './ChatMessage.vue'
import { GoogleGenAI } from '@google/genai'
import thinkingDots from '../../public/thinkingDots.gif'

const props = defineProps({
  isOpen: Boolean
})
const emit = defineEmits(['close'])

const ai = new GoogleGenAI({
  apiKey: import.meta.env.VITE_GEMINI_API_KEY,
})

async function askAI(message) {
  const response = await ai.models.generateContent({
    model: 'gemini-2.5-flash',
    contents: message,
  })
  return response.text
}

function closeChat() {
  emit('close')
}

const inputText = ref('')
const chatBody = ref(null)
const loading = ref(false)

const messageList = ref([
  {
    sender: 'bot',
    message: 'Hello, how can I help you?',
  },
])

function scrollToBottom({ behavior = 'smooth' } = {}) {
  nextTick(() => {
    if (!chatBody.value) return
    try {
      chatBody.value.scrollTo({ top: chatBody.value.scrollHeight, behavior })
    } catch (e) {
      console.error(e)
      chatBody.value.scrollTop = chatBody.value.scrollHeight
    }
  })
}

watch(
  () => props.isOpen,
  (open) => {
    if (open) scrollToBottom({ behavior: 'auto' })
  },
)

watch(
  () => messageList.value.length,
  () => {
    if (props.isOpen) scrollToBottom({ behavior: 'smooth' })
  },
)

onMounted(() => {
  if (props.isOpen) scrollToBottom({ behavior: 'auto' })
})
function sendMessage() {
  if (!inputText.value.trim()) return
  loading.value = true
  const messageToSend = inputText.value
  const userMessage = { sender: 'user', message: messageToSend }
  messageList.value.push(userMessage)
  askAI(
    'Eres un ChatBot y estás en una ventana de chat en el sitio web de Pablo, un programador frontend excepcional. Pablo te ha puesto a cargo de los visitantes de su portfolio, para que les orientes y resuelvas sus dudas. Los clientes o empleadores pueden encontrar los datos de contacto fácilmente, y también pueden descargar el CV de Pablo y ver sus proyectos, así como las tecnologías principales que utiliza. Además, pueden encontrar iconos con enlace a LinkedIn y GitHub en la parte superior de la página web, a la derecha (en el navbar). Responde brevemente en el mismo idioma en el que te escriba a continuación: ' +
      inputText.value,
  )
    .then((response) => {
      messageList.value.push({ sender: 'bot', message: response })
    })
    .catch((error) => {
      console.log('Error: ', error)
    })
    .finally(() => {
      loading.value = false
    })
  inputText.value = ''
}
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
    <div v-if="loading" class="thinking">
      <div class="thinking-inner">
        <img :src="thinkingDots" alt="La IA está pensando..." class="thinking-dots" />
      </div>
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
.thinking {
  display: flex;
  justify-content: flex-start;
  padding: 4px 0;
}

.thinking-dots {
  width: 50px;
  height: auto;
  display: block;
}

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
  bottom: 180px;
  right: 120px;
  width: 420px;
  height: 520px;
  background: #fff;
  border-radius: 16px;
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.3);
  display: flex;
  flex-direction: column;
  overflow: hidden;
  z-index: 1000;
}

.chat-header {
  background: var(--midnight-purple);
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

@media (max-width: 1024px) {
  .chat-window {
    top: 50%;
    left: 50%;
    bottom: auto;
    right: auto;
    transform: translate(-50%, -50%);
    width: 80%;
    max-width: 600px;
    height: 70%;
    max-height: 500px;
  }
}

@media (max-width: 600px) {
  .chat-window {
    bottom: 0;
    right: 0;
    width: 100vw;
    height: 100vh;
    border-radius: 0;
  }

  .chat-header h3 {
    font-size: 1.2rem;
  }

  .chat-footer input {
    font-size: 0.9rem;
  }

  .chat-footer button {
    font-size: 0.9rem;
  }
}
</style>
