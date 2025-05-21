<script setup>
import { ref} from 'vue'
import ProductDisplay from './components/ProductDisplay.vue'
import ProductDetails from './components/ProductDetails.vue'

const cart = ref(0)
// const premium = ref(true);
const premium = ref(false);
</script>
  
<template>
  <div class="nav-bar"></div>
  <div class="cart">Cart({{ cart }})</div>
  <ProductDisplay :premium="premium"/>   
</template>