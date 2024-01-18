<script setup>
  import { ref, onMounted } from 'vue';

  const showBlock = ref(false);
  const startTime = ref(0);
  const reactionTime = ref(0);

  const props = defineProps(['delay']);

  function startTimer() {
    startTime.value = Date.now();
  }

  function stopTimer() {
    reactionTime.value = Date.now() - startTime.value;
    // console.log(`${reactionTime.value / 1000} seconds`);
  }

  onMounted(() => {
    setTimeout(() => {
      showBlock.value = true;
      console.log(props.delay);
      startTimer();
    }, props.delay);
  });
</script>

<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    Click Me!
  </div>
</template>

<style scoped>
  .block {
    width: 400px;
    border-radius: 20px;
    background: #0faf87;
    color: #fff;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
  }
</style>
