<script setup>
  import { ref } from 'vue';
  import Block from './components/Block.vue';

  const isPlaying = ref(false);
  const delay = ref(null);

  function start() {
    delay.value = 2000 + Math.random() * 5000;
    isPlaying.value = true;
    console.log(delay.value);
  }
</script>

<template>
  <h1>Reaction Ninja</h1>
  <button @click="start" :disabled="isPlaying">play</button>
  <Block v-if="isPlaying" :delay="delay" />
</template>

<style scoped>
</style>
