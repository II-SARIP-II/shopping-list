<template>
  <input :type="type" :placeholder="placeholder" v-model="model" >
</template>



<script setup>
const props = defineProps({
  type: String,
  placeholder: String
})

const model = defineModel()
</script>



<style scoped>
input {
  background-color: #181818;
  color: white;
  padding: 0.5em;
  line-height: 1em;
  border-radius: 0.6em;
  font-size: 1rem;
  border: 2px solid white;
  outline: none;
  width: 10rem;
  box-shadow: rgba(255, 255, 255, 0.50) 0px 3px 8px;
  text-shadow: rgba(255, 255, 255, 0.50) 0px 3px 8px;

}

input:hover {
}

</style>
