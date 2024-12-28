<script setup>
import { ref } from 'vue'
import canciones from '../canciones.json'  // Asegúrate de que la ruta sea correcta
import HelloWorld from './components/HelloWorld.vue'
import Lista from './components/Lista.vue'
import Letra from './components/Letra.vue'

const selectedSong = ref(null);

// Cambiar la búsqueda por nombre directamente
const selectSong = (song) => {
  selectedSong.value = canciones[song];  // Usamos el nombre de la canción para acceder al objeto
};

const goBack = () => {
  selectedSong.value = null;
};
</script>

<template>
  <header>
    <img alt="logo" class="logo" src="./assets/logo.svg" width="125" height="125" />
    <div class="wrapper">
      <HelloWorld msg="Hola" />
    </div>
  </header>

  <main>
    <div>
      <!-- Transición suave entre la lista y la letra -->
      <transition name="fade" mode="out-in">
        <div :key="selectedSong ? 'letra' : 'lista'">
          <!-- Mostrar Lista o Letra según el estado -->
          <Lista v-if="!selectedSong" @select="selectSong" />
          <Letra v-else :song="selectedSong" @back="goBack" />
        </div>
      </transition>
    </div>
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}

/* Transición de desvanecimiento */
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter, .fade-leave-to {
  opacity: 0;
}
</style>
