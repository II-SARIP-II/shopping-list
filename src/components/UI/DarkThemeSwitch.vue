<template>
  <div class="dark-theme-switch" @click="toggle">
    <vue-feather v-if="dark" type="moon" />
    <vue-feather v-else type="sun" />
  </div>
</template>



<script setup>
import {computed, onMounted} from 'vue'
import store from '@/store'

const dark = computed(()=>store.dark)

function toggle () {
  localStorage.setItem('tp_ui-dark-theme', (dark.value) ? 'light' : 'dark')
  store.dark = !store.dark
}

onMounted(() => {
  if (localStorage.getItem('tp_ui-dark-theme')) {
    store.dark = localStorage.getItem('tp_ui-dark-theme') === 'dark'
  }
})
</script>



<style scoped>
div {
  display: inline-block;
  cursor: pointer;
  margin-left: 0.5em;
}
</style>
