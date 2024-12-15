<script setup>
import WelcomeItem from './WelcomeItem.vue';
import NotaIcon from './icons/IconNota.vue';

// Lista de canciones
const canciones = [
  'Ángeles cantando están',
  'Al mundo paz',
  'Ya repican las campanas',
  'Venid pastorcillos',
  'Noche de paz',
  'El amor de Jesús',
];
</script>

<template>
  <div>
    <WelcomeItem
        v-for="(cancion, index) in canciones"
        :key="index"
        @click="$emit('select', cancion)"
    >
      <template #icon>
        <NotaIcon />
      </template>
      <template #heading>{{ cancion }}</template>
    </WelcomeItem>
  </div>
</template>
