<template>
  <div>
      <label v-for="option of options" :key="option.value">
        <input
          type="radio"
          :value="option.value"
          v-model="model"
       >
        {{ option.name }}
      </label>
  </div>
</template>



<script setup>
const props = defineProps({
  options: Array,
  modelValue: Object
})

const model = defineModel()
</script>



<style scoped>


label {
  display: block;
  line-height: 1.3em;
}
</style>
