<script setup>
import { ref } from 'vue'
import socksGreenImage from './assets/images/socks_green.jpeg';

const product = ref('Socks');
const productImage = ref(socksGreenImage);
const productUrl = ref('url');

</script>

<template>
  <div class="nav-bar">
    <div class="product-display">
      <div class="product-container">
        <div class="product-image">
          <!-- image goes here -->
           <!-- ubound image -->
           <!-- <img src="socksGreenImage" alt="" srcset="">  -->

           <!-- bound image to non-reactive variable -->
           <!-- <img v-bind:src="socksGreenImage" alt="" srcset="">  -->

           <!-- bound image to reactive variable -->
           <img v-bind:src="productImage" alt="" srcset=""> 
            <a :href="productUrl"></a>
        </div>
        <div class="product-info">
          <h1>{{ product }}</h1>
        </div>
      </div>
    </div>
  </div>
</template>