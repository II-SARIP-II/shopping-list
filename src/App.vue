<script setup>
import BaseButton from './components/UI/BaseButton.vue';
import BaseInput from './components/UI/BaseInput.vue';
import BaseRadioButton from "@/components/UI/BaseRadioButton.vue";
import BaseSelect from "@/components/UI/BaseSelect.vue";
import CaTemplate from "@/components/UI/CaTemplate.vue";
import {ref} from 'vue';
import CatListe from "@/components/UI/CatListe.vue";
import ToBuyTemplate from "@/components/UI/ToBuyTemplate.vue";

const options = ref({
  1: {
    id: 1,
    name: 'cat-sseroles',
    description: 'the hottest cat on earth',
    price: 1000,
    picture: '/src/assets/cat-serroles.png',
  },
  2: {
    id: 2,
    name: 'khachapuri',
    description: 'this is a cat from Géorgia',
    price: 200,
    picture: '/src/assets/chat-georgien.png',
  },
  3: {
    id: 3,
    name: 'chapiteau',
    description: 'This cat is a clown',
    price: 60065,
    picture: '/src/assets/chat-clown.png',
  },
  4: {
    id: 4,
    name: 'chatain',
    description: 'a brown cat',
    price: 100,
    picture: '/src/assets/chat-thym.png',
  },
  5: {
    id: 5,
    name: 'chasseur',
    description: 'He shoots on other animals',
    price: 1,
    picture: '/src/assets/chat-soeur.png',
  },
  6: {
    id: 6,
    name: 'chapeau',
    description: 'Slytherin or Gryffondor',
    price: 1010,
    picture: '/src/assets/chat-peau.png',
  },
  7: {
    id: 7,
    name: 'chameau',
    description: "He loves sand and oasis",
    price: 1020,
    picture: '/src/assets/chat-meau.png',
  },
  8: {
    id: 8,
    name: 'chacal',
    description: "Is this a cat ???",
    price: 2020,
    picture: '/src/assets/chat-cale.png',
  },
  9: {
    id: 9,
    name: 'challenge',
    description: "He never gives up",
    price: 20,
    picture: '/src/assets/chat-llenge.png',
  },
  10: {
    id: 10,
    name: 'charmante',
    description: "Every male loves her",
    price: 120,
    picture: '/src/assets/chat-remante.png',
  },
  11: {
    id: 11,
    name: 'chateigne',
    description: "his hairs are like hedgehog spike",
    price: 10,
    picture: '/src/assets/chat-teigne.png',
  },
  12: {
    id: 12,
    name: 'chaleur',
    description: "hottest cat on earth",
    price: 1020,
    picture: '/src/assets/chat-leur.png',
  },
});

const cartItems = ref([]);

const addToCart = (item) => {
  cartItems.value.push(item);
};

const updateOptions = (id) => {
  const newName = prompt('Enter new name:');
  if (newName) {
    options.value[id].name = newName;
  }
};
</script>

<template>
  <main>
    <section class="ToBuy">
      <h1 class="title">À ACHETER</h1>
      <ToBuyTemplate :cartItems="cartItems" @update-options="updateOptions"/>
    </section>
    <hr class="separator">
    <section class="AllItems">
      <h1 class="title">AJOUTER UN CHAT</h1>
      <CatListe :options="options" @add-to-cart="addToCart"/>
    </section>
  </main>
</template>

<style scoped>
main {
  display: flex;
  justify-content: space-around;
}

main section {
  width: 50%;
  display: flex;
  align-items: center;
  flex-direction: column;
}

.title {
  margin-bottom: 30px;
  color: white;
  text-shadow: rgba(255, 255, 255, 0.50) 0px 3px 8px;
}

.separator {
  color: white;
  width: 1px;
  height: 500px;
  align-self: center;
}
</style>
