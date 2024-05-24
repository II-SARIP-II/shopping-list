<template>
  <div>
    <label for="fontSelector">Font : </label>
    <select v-model="selected" @change="emitSelection">
      <option v-for="item in values" :key="item">
        {{ item }}
      </option>
    </select>
  </div>
</template>

<script setup>
import { ref, defineEmits } from 'vue';

const values = ["Default","Dellova", "Open Dyslexic"];

const selected = ref(values[0]);

const emit = defineEmits(['font']);
const emitSelection = () => {
  emit('font', selected.value);
};
</script>

<style>
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
  width: 150px;
}
</style>


<style>
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
  width: 150px;
}

</style>