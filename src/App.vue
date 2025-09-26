<script setup>
import { RouterLink, RouterView } from 'vue-router'
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import { faHouse } from '@fortawesome/free-solid-svg-icons'
import { faLinkedin, faSquareGithub } from '@fortawesome/free-brands-svg-icons'
import ChatButton from './components/ChatButton.vue'

function abrirEnlace(url) {
  window.open(url, "_blank", "noopener,noreferrer");
}
</script>

<template>
  <header>
      <nav class="nav-bar">
        <div>
          <RouterLink to="/" class="icon-link"><font-awesome-icon class="icon" :icon="faHouse" /></RouterLink>
        </div>
        <div>
          <button class="icon-button" @click="abrirEnlace('https://www.linkedin.com/in/pablo-vacas-macarro-518542358/')"><FontAwesomeIcon class="icon" :icon="faLinkedin" /></button>
          <button class="icon-button" @click="abrirEnlace('https://github.com/pablov-git')"><FontAwesomeIcon class="icon" :icon="faSquareGithub" /></button>
        </div>
      </nav>
  </header>

  <main>
    <RouterView />
    <div style="height: 100px;"></div>
  </main>

  <footer>
    <p>@ 2025</p>
    <ChatButton/>
  </footer>
</template>

<style scoped>
header {
  display: flex;
  flex-direction: row;
  justify-content: center;
  width: 100%;
}

.icon-button {
  background: none;
  border: none;
  cursor: pointer;
  padding: 0.5rem;
  font-size: 1.8rem;
  color: var(--floral-white);
  transition: transform 0.2s ease;
}

.icon-button:hover {
  transform: scale(1.1);
  color: var(--sky);
}

.icon{
  width: 30px;
  height: 30px;
}

.icon-link {
  display: inline-block;
  cursor: pointer;
  padding: 0.5rem;
  font-size: 1.8rem;
  color: var(--floral-white);
  transition: transform 0.2s ease, color 0.2s ease;
}

.icon-link:hover {
  transform: scale(1.1);
  color: var(--sky);
}

.nav-bar {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  background-color: var(--eerie-black);
  width: 90%;
  margin-top: 30px;
}

nav a.router-link-exact-active {
  color: var(--floral-white);
}

nav a.router-link-exact-active:hover {
  color: var(--sky);
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid rgb(143, 91, 216);
  color: var(--timberwolf);
  text-decoration: none;
}

nav a:first-of-type {
  border: 0;
}

footer {
  position: fixed;
  bottom: 0;
  left: 0;
  width: 100%;
  background: var(--eerie-black);
  color: var(--floral-white);
  padding: 1rem;
  display: flex;
  justify-content: center;
  align-items: center;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
