<script setup>
  import { ref, onMounted } from 'vue';

  const props = defineProps(['score']);

  const rank = ref(null);

  onMounted(() => {
    if (props.score < 250) {
      rank.value = 'Ninja Fingers';
    } else if (props.score < 400) {
      rank.value = 'Rapid Reflexes.';
    } else {
      rank.value = 'Snail Pace...';
    }
  });
</script>

<template>
   <p>Reaction Time: {{ score }} ms</p>
   <p class="rank">{{ rank }}</p>
</template>

<style scoped>
  .rank {
    font-size: 1.4em;
    color: #0faf87;
    font-weight: bold;
  }
</style>
