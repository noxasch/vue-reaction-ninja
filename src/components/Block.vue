<script setup>
  import { ref, onMounted } from 'vue';

  const showBlock = ref(false);
  const props = defineProps(['delay']);

  onMounted(() => {
    setTimeout(() => {
      showBlock.value = true;
      console.log(props.delay);
    }, props.delay);
  });
</script>

<template>
  <div class="block" v-if="showBlock"></div>
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
