<template>
  <img :src="iconPath" alt="Mi icono" width="20" height="20">
</template>

<script>
export default {
  data() {
    return {
      iconPath: new URL('@/assets/nota.svg', import.meta.url).href,
    };
  },
};
</script>