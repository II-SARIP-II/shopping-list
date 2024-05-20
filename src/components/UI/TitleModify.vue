<template>
  <img src="/src/assets/pen.png" height="15px" @click="modifyTitle">
</template>

<script setup>
import { defineEmits } from 'vue';

const emit = defineEmits(['modify-title']);

const modifyTitle = () => {
  emit('modify-title');
};
</script>
<style scoped>

</style>