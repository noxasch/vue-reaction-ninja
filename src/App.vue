<script setup>
  import { ref } from 'vue';
  import Block from './components/Block.vue';

  const isPlaying = ref(false);
  const delay = ref(null);
  const score = ref(0);

  function start() {
    delay.value = 2000 + Math.random() * 5000;
    isPlaying.value = true;
  }

  function gameOver(reactionTime) {
    score.value = reactionTime;
    isPlaying.value = false;
    delay.value = null;
  }
</script>

<template>
  <h1>Reaction Ninja</h1>
  <button @click="start" :disabled="isPlaying">play</button>
  <Block v-if="isPlaying" :delay="delay" @game-over="gameOver" />
  <p v-if="!isPlaying">Reaction Time: {{ score }} ms</p>
</template>

<style scoped>
</style>
