<script setup>
import { ref } from 'vue'

const contact = ref({
  name: '',
  email: '',
  message: '',
})

const sendEmail = (e) => {
  e.preventDefault()
  console.log(contact.value)
  if (!contact.value.name || !contact.value.email || !contact.value.message) {
    alert('Por favor, rellena todos los campos')
    return
  }
  if (!contact.value.email.includes('.')) {
    alert('El email no es válido')
    return
  }
  if (contact.value.message.length < 10) {
    alert('El mensaje debe tener al menos 10 caracteres')
    return
  }
  fetch('https://formspree.io/f/mqadjzzd', {
    method: 'POST',
    body: JSON.stringify(contact.value),
    headers: {
      Accept: 'application/json',
    },
  })
    .then((response) => {
      if (response.ok) {
        contact.value = {
          name: '',
          email: '',
          message: '',
        }
      }
      alert('Mensaje enviado con éxito')
    })
    .catch((error) => {
      console.log(error)
      alert('Hubo un error al enviar el mensaje')
    })
}
</script>

<template>
  <div class="contact-container">
    <div class="contact-grid">
      <aside class="contact-left">
        <h1 class="title">Contacto</h1>
        <p class="lead">Por favor, rellena el formulario y te contactaré lo antes posible</p>
      </aside>

      <div class="contact-right">
        <form v-on:submit="sendEmail" class="contact-form" aria-label="Formulario de contacto">
          <div class="form-group">
            <label for="name">Nombre</label>
            <input v-model="contact.name" type="text" id="name" placeholder="Tu nombre" />
          </div>

          <div class="form-group">
            <label for="email">Correo electrónico</label>
            <input
              v-model="contact.email"
              type="email"
              id="email"
              placeholder="tucorreo@ejemplo.com"
            />
          </div>

          <div class="form-group">
            <label for="message">Mensaje</label>
            <textarea
              v-model="contact.message"
              id="message"
              rows="5"
              placeholder="Escribe tu mensaje aquí..."
            ></textarea>
          </div>

          <button type="submit" class="submit-btn">Enviar</button>
        </form>
      </div>
    </div>
  </div>
</template>

<style scoped>
.contact-container {
  max-width: 980px;
  margin: 2rem auto;
  padding: 1rem;
}

.contact-grid {
  display: grid;
  grid-template-columns: 38% 62%;
  gap: 2rem;
  align-items: start;
}

.contact-left .title {
  margin: 0 0 0.6rem 0;
  font-size: 2rem;
  line-height: 1.05;
}

.contact-left .lead {
  margin: 0;
  font-size: 1rem;
  opacity: 0.9;
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.form-group {
  display: flex;
  flex-direction: column;
}

.form-group label {
  font-weight: 600;
  margin-bottom: 0.3rem;
}

.form-group input,
.form-group textarea {
  border: none;
  border-bottom: 1px solid var(--floral-white);
  background: transparent;
  padding: 0.5rem 0;
  font-size: 1rem;
  transition: border-color 0.3s ease;
}

.form-group input::placeholder,
.form-group textarea::placeholder {
  color: var(--floral-white);
}

.form-group input:focus,
.form-group textarea:focus {
  outline: none;
  border-bottom: 1px solid var(--floral-white);
}

.submit-btn {
  margin-top: 0.5rem;
  padding: 0.6rem 1.2rem;
  border-radius: 6px;
  border: none;
  cursor: pointer;
  background: var(--floral-white);
  color: var(--black-olive);
  font-weight: 600;
  transition: background 0.3s ease;
}

.submit-btn:hover {
  color: var(--floral-white);
  background: var(--sky);
}

@media (max-width: 720px) {
  .contact-grid {
    grid-template-columns: 1fr;
  }
}
</style>
