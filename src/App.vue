<script setup>
import { ref } from 'vue'
import socksGreenImage from './assets/images/socks_green.jpeg'

const product = ref('Socks')
const image = ref(socksGreenImage)
// const inStock = ref(true); //instock
// const inStock = ref(false); //out of stock

// invetory ref
// const invetory = ref(100); //instock value
const invetory = ref(9); //almost sold out value

// const onSale = ref(false);
const onSale = ref(true);
</script>
  
<template>
  <div class="nav-bar"></div>
  <div class="product-display">
    <div class="product-container">
      <div class="product-image">    
        <img v-bind:src="image">
      </div>
      <div class="product-info">
        <h1>{{ product }}</h1>
        <p v-if="invetory > 20">In Stock</p>
        <p v-else-if="invetory <=10 && invetory > 0">Almost sold out</p>
        <p v-else>Out of Stock</p>

        <p v-if="onSale">On Sale</p>
      </div>
    </div>
  </div>
</template>