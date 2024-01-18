<script setup>
  import { ref } from 'vue';
  import Block from './components/Block.vue';
  import Results from './components/Results.vue';

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
  <Results v-if="!isPlaying" :score="score" />
</template>

<style scoped>
  button {
    background: #0faf87;
    color: #fff;
    border: none;
    padding: 8px 16px;
    border-radius: 4px;
    font-size: 16px;
    letter-spacing: 1px;
    cursor: pointer;
    margin: 10px;
  }

  button[disabled] {
    opacity: 0.2;
    cursor: not-allowed;
  }
</style>
