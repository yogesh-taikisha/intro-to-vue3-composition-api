<script setup>
import { ref, computed } from 'vue'
import socksGreenImage from './assets/images/socks_green.jpeg'
import socksBlueImage from './assets/images/socks_blue.jpeg'

const product = ref('Socks')
const brand = ref('Vue Mastery')

// const image = ref(socksGreenImage)
const image = computed(() => {
  // console.log(variants.value);
  console.log('selected variant', selectedVariant.value);
  return variants.value[selectedVariant.value].image
});

const selectedVariant = ref(0);

// const inStock = ref(false)
const inStock = computed(() => {
  return variants.value[selectedVariant.value].quantity > 0
});

  
const details = ref(['50% cotton', '30% wool', '20% polyester'])

const variants = ref([
  { id: 2234, color: 'green', image: socksGreenImage, quantity: 50 },
  { id: 2235, color: 'blue', image: socksBlueImage, quantity: 0 },
])

const cart = ref(0)

const addToCart = () => cart.value += 1

// const updateImage = (variantImage) => image.value = variantImage
// const title = computed(()=> {
//   return brand.value + '' + product.value;
// });

const updateVariant = (index) => {
  selectedVariant.value = index;
  // console.log(index);
};

const title = computed(()=> {
  return brand.value + '' + product.value;
});

const onSale = ref(true);
// const onSale = ref(false);

const saleTitle = computed(() => {
  return brand.value + ' is on sale' 
})
</script>
  
<template>
  <div class="nav-bar"></div>
  <div class="cart">Cart({{ cart }})</div>
  <div class="product-display">
    <div class="product-container">
      <div class="product-image">    
        <img v-bind:src="image">
      </div>
      <div class="product-info">

        <!-- <h1>{{ product }}</h1> -->
        <!-- <h1>{{ brand + '' + product }}</h1> -->
        <h1 v-if="onSale">{{ saleTitle }}</h1>
        <h1 v-else>{{ title }}</h1>

        <p v-if="inStock">In Stock</p>
        <p v-else>Out of Stock</p>
        <ul>
          <li v-for="detail in details">{{ detail }}</li>
        </ul>

        <!-- to change the image based on the color selection -->
        <!-- <div 
          v-for="variant in variants" 
          :key="variant.id"
          @mouseover="updateImage(variant.image)"
          class="color-circle"
          :style="{ backgroundColor: variant.color }"
        > -->

        <!-- to change the stock out and in stock based on the individual quantity of the colored socks; major change is the new method on the click of the mousehover on the colored circles -->
        <div 
          v-for="(variant, index) in variants" 
          :key="variant.id"
          @mouseover="updateVariant(index)"
          class="color-circle"
          :style="{ backgroundColor: variant.color }"
        >
        </div>

        <button
          class="button" 
          :class="{ disabledButton: !inStock }"
          :disabled="!inStock"
          v-on:click="addToCart"
        >
          Add to cart
        </button>
      </div>
    </div>
  </div>
</template>