<template>
  <div class="cart-container">
    <h2 style="margin-bottom: 20px">Shopping Cart</h2>
    <div v-if="cartItems.length === 0">Your cart is empty.</div>
    <div v-else>
      <div v-for="item in cartItems" :key="item.id" class="loop">
        <hr class="top-line">
        <div class="cart-item">
          <img :src="item.picture" alt="Picture" class="item-picture"/>
          <div class="item-details">
            <div style="display: flex; gap: 10px; align-items: center">
              <h3 class="item-name" :class="{ 'strikethrough': item.isStriked }" @click="striped(item.id)">{{ item.name }}</h3>
                <TitleModify @modify-title="updateTitle(item.id)"></TitleModify>
            </div>
            <div style="display: flex; justify-content: space-around; height: 40px; align-items: center">
              <p class="item-price">{{ item.price }}$</p>
              <DeleteArticle @delete-article="deleteArticle(item.id)"></DeleteArticle>
            </div>
          </div>
          <div>
            <BaseSelect v-model="item.quantity" @update:selected="updateSelected(item, $event)"/>
          </div>
        </div>
      </div>
      <div class="cart-total">
        <hr>
        <h3>Total: {{ cartTotal }}$</h3>
      </div>
    </div>
  </div>
</template>

<script setup>
import {ref, computed} from 'vue';
import {defineProps, defineEmits} from 'vue';
import BaseSelect from './BaseSelect.vue';
import TitleModify from "@/components/UI/TitleModify.vue";
import DeleteArticle from "@/components/UI/DeleteArticle.vue";

const props = defineProps({
  cartItems: Array,
});

const emit = defineEmits(['update-options']);

const updateSelected = (item, value) => {
  item.quantity = value;
};

const cartTotal = computed(() => {
  return props.cartItems.reduce((total, item) => {
    return total + (item.price * (item.quantity ? item.quantity : 1));
  }, 0);
});

const updateTitle = (id) => {
  emit('update-options', id);
};
const deleteArticle = (id) => {
  const index = props.cartItems.findIndex(item => item.id === id);
  if (index !== -1) {
    props.cartItems.splice(index, 1);
  }
};

const striped = (id) => {
  const item = props.cartItems.find(item => item.id === id);
  if (item) {
    item.isStriked = !item.isStriked;
  }
};
</script>


<style scoped>
.cart-container {
  border: 1px solid #ccc;
  border-radius: 10px;
  padding: 20px;
  width: 300px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.cart-item {
  display: flex;
  align-items: center;
  margin: 10px 0 10px 0;
  justify-content: space-around;
}

.item-picture {
  width: 50px;
  height: auto;
  margin-right: 10px;
}

.item-details {
  display: flex;
  flex-direction: column;
}

.top-line {
  width: 80%;
  margin: 20px 0 20px 0;
}

.item-name {
  font-size: 1.2em;
  margin: 0;
}

.item-price {
  font-size: 1em;
  font-weight: bold;
}

.strikethrough {
  text-decoration: line-through;
}
</style>
