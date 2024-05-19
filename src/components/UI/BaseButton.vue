<template>
  <button :disabled="inactive">
    <slot></slot>
  </button>
</template>

<script setup>
const props = defineProps({
  inactive: Boolean
})
</script>



<style scoped>
button {
  padding: 0.5em 1.25em;
  margin-right: 0.5em;
  line-height: 1.2em;
  border-radius: 1.2em;
  border: none;
  font-size: 1.2rem;
  color: white;
  background-color: #0077ff;
  transition: background-color 0.5s, transform 0.05s;
}

button:hover {
  background-color: #0060ca;
  cursor: pointer;
}

button:not([disabled]):active {
  transform: translate(1px, 1px);
}
/** Error **/
button.error {
  background-color: red;
  color: black;
  font-weight: 800;
}

button:hover.error{
  background-color: #d10000;
}

/** Secondary **/
button.secondary {
  background-color: #181818;
  border: 1px solid white;
  font-weight: 500;
  transition: 0.2s;
  box-shadow: rgba(255, 255, 255, 0.50) 0px 3px 8px;
text-shadow: rgba(255, 255, 255, 0.50) 0px 3px 8px;

}

button:hover.secondary{
  background-color: rgb(255,255,255, 0.10);
  transition: 0.2s;
}

</style>
