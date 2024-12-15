<script setup>
import {defineProps} from 'vue'

const props = defineProps({
  song: {
    type: Object,
    required: true
  }
})
</script>

<template>
  <div>
    <h1>{{ song.titulo }}</h1>
    <div v-for="(section, index) in song.orden" :key="index">
      <!-- Renderiza las estrofas y el coro en el orden adecuado -->
      <p v-if="typeof section === 'number'" :style="{ whiteSpace: 'pre-line' }">{{ song.estrofas[section] }}</p>
      <p v-if="section === 'coro'" :style="{ whiteSpace: 'pre-line' }">{{ song.coro }}</p>
    </div>
    <button @click="$emit('back')">Volver</button>
  </div>
</template>

<style scoped>
p {
  color: #42b983;
}
</style>
