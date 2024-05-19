<template>
  <select v-model="selected" @change="emitSelection">
    <option v-for="item in numbers" :key="item">
      {{ item }}
    </option>
  </select>
</template>

<script setup>
import { ref, defineEmits } from 'vue';

const numbers = [1, 2, 3, 4, 5];

const selected = ref(numbers[0]);

const emit = defineEmits(['update:selected']);
const emitSelection = () => {
  emit('update:selected', selected.value);
};
</script>

<style scoped>
select {
  background: #181818;
  color: white;
  padding: 0.5em;
  border-radius: 0.6em;
  font-size: 1rem;
  border: 1px solid white;
  box-shadow: rgba(255, 255, 255, 0.50) 0px 3px 8px;
  text-shadow: rgba(255, 255, 255, 0.50) 0px 3px 8px;
  outline: none;
  cursor: pointer;
  width: 60px;
}


</style>
