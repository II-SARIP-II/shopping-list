<template>
  <vue-feather type="trash-2" style="cursor: pointer" @click="deleteItem"></vue-feather>
</template>

<script setup>
import VueFeather from 'vue-feather';
import { defineEmits } from 'vue';

const emit = defineEmits(['delete-article']);

const deleteItem = () => {
  emit('delete-article');
};
</script>

<style scoped>

</style>