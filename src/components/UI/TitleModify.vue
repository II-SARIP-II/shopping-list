<template>
  <vue-feather type="edit-2" @click="modifyTitle" style="height: 15px; cursor: pointer"></vue-feather>
</template>

<script setup>

import { defineEmits } from 'vue';
import VueFeather from 'vue-feather';
const emit = defineEmits(['modify-title']);

const modifyTitle = () => {
  emit('modify-title');
};
</script>

<style scoped>
  vue-feather{

  }
</style>