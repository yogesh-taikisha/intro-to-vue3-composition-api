<script setup>
import { ref } from 'vue';

const product = ref('Frido Active Socks');
const productDescription = ref('Dual-Layer Moisture Control & Anti-Odor Design');
</script>

<template>
  <div class="product-display">
    <div class="product-container">
      <div class="product-info">
        <h1>{{ product}}</h1>
        <p>{{ productDescription }}</p>
      </div>
    </div>
  </div>
</template>