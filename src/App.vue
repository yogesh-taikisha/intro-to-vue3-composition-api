<script setup>
import { ref } from 'vue'
import ProductDisplay from '@/components/ProductDisplay.vue'

// const cart = ref(0);
const cart = ref([]);
const premium = ref(true)

// const updateCart = () => {
//   cart.value += 1
// };
const updateCart = (id) => {
  cart.value.push(id)
};

const removeFromCart = (id) => {
  cart.value.pop(id)
}

</script>
  
<template>
  <div class="nav-bar"></div>
  <!-- <div class="cart">Cart({{ cart }})</div> -->
  <div class="cart">Cart({{ cart.length }})</div>
  <ProductDisplay :premium="premium" @add-to-cart="updateCart" @remove-from-cart="removeFromCart"></ProductDisplay>
</template>