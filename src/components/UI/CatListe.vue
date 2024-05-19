<template>
  <div class="list-container">
    <CaTemplate v-for="option in Object.values(options)" :key="option.id" :option="option" @add-to-cart="addToCart" />
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';
import CaTemplate from './CaTemplate.vue';

const props = defineProps({
  options: Object,
});

const emit = defineEmits(['add-to-cart']);

const addToCart = (item) => {
  emit('add-to-cart', item);
};
</script>

<style scoped>
.list-container {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  justify-content: center;
}
</style>