<script setup>
defineProps({
  sender: String,
  message: String,
})
</script>

<template>
  <div class="message-row" :class="sender === 'user' ? 'user' : 'bot'">
    <!-- Avatar -->
    <div class="avatar">
      <span>{{ sender == 'user' ? '👤' : '🤖' }}</span>
    </div>

    <!-- Burbuja -->
    <div :class="sender == 'user' ? 'message-user' : 'message-bot'">
      {{ message }}
    </div>
  </div>
</template>

<style scoped>
/* Contenedor que junta avatar + burbuja */
.message-row {
  display: flex;
  align-items: flex-end;
  margin-bottom: 12px;
  width: 100%;
  box-sizing: border-box;
  gap: 8px;
  padding: 0 2px;
}

.message-row.user {
  display: flex;
  justify-content: flex-end;
  flex-direction: row;
  width: 100%;
  align-items: flex-end;
  gap: 8px;
}

.message-row.bot {
  justify-content: flex-start;
  flex-direction: row;
}


/* Avatar */
.avatar {
  width: 36px;
  height: 36px;
  border-radius: 50%;
  background-color: #eee;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 18px;
  flex-shrink: 0;
}

/* Burbujas */
.message-user {
  background-color: #007bff;
  color: #fff;
  padding: 10px 14px;
  border-radius: 12px;
  max-width: 70%;
  word-wrap: break-word;
  text-align: left;
}

.message-bot {
  background-color: #8e1790;
  color: #fff;
  padding: 10px 14px;
  border-radius: 12px;
  max-width: 70%;
  word-wrap: break-word;
  text-align: left;
}
</style>
