<template>
  <div class="item-card">
    <img :src="option.picture" alt="Picture" class="item-picture"/>
    <div class="item-details">
      <h3 class="item-name">{{ option.name }}</h3>
      <p class="item-description">{{ option.description }}</p>
      <p class="item-price">{{ option.price }}$</p>
      <BaseButton class="secondary" @click="addToCart(option)">Add to Cart</BaseButton>
    </div>
  </div>
</template>

<script setup>
import BaseButton from "@/components/UI/BaseButton.vue";
import { defineProps, defineEmits } from 'vue';

const props = defineProps({
  option: Object,
});

const emit = defineEmits(['add-to-cart']);

const addToCart = (item) => {
  emit('add-to-cart', item);
};
</script>


<style scoped>
.item-card{
  background-color: #181818;
  height: 200px;
  color: white;
  border: 1px solid white;
  border-radius: 10px;
  padding: 20px;
  width: 300px;
  box-shadow: rgba(255, 255, 255, 0.50) 0px 3px 8px;
  text-shadow: rgba(255, 255, 255, 0.50) 0px 3px 8px;
  display: flex;
  justify-content: space-between;
  flex-wrap: nowrap;
  align-items: center;
}

.item-picture{
  height: 100px;
  display: block;
  position: relative;
  filter: drop-shadow(1px 0 3px white);
}


.secondary{
  height: 30px;
  font-size: 1em;
}
.item-details{
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: flex-start;
  padding-left: 20px;
}


</style>
