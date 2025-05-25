<!-- template literal -->
<template>
  <form class="review-form" @submit.prevent="onSubmit">
    <h3>Leave a review</h3>
    <label for="name">Name:</label>
    <input id="name" v-model="review.name">

    <label for="review">Review:</label>      
    <textarea id="review" v-model="review.content"></textarea>

    <label for="rating">Rating:</label>
    <select id="rating" v-model.number="review.rating">
      <option>5</option>
      <option>4</option>
      <option>3</option>
      <option>2</option>
      <option>1</option>
    </select>
    
    <label for="recommendation">Recommendation:</label>
    <select id="recommendation" v-model="review.recommendation">
      <option>Yes</option>
      <option>No</option>
    </select>

    <input class="button" type="submit" value="Submit">

  </form>
</template>

<!-- we need to need bind the form inputs to some reactive state  -->
<script setup>
import { reactive } from 'vue';

const emit = defineEmits(['review-submitted'])

const review = reactive(
  {
    name: '',
    content: '',
    rating: null,
    recommendation: ''
  }
);

const onSubmit = () => {
  // form validation
  if(review.name === '' || review.content === '' || review.rating === null) {
    alert('Review is incomplete. Please fill out every field.')
    return
  };

  const productReview = {
    name: review.name,
    content: review.content,
    rating: review.rating,
    recommendation: review.recommendation
  }

  emit('review-submitted', productReview);
  // product Review is passed along as a payload

  // clearing the product review form
  review.name = ''
  review.content = ''
  review.rating = null,
  recommendation = ''
};
</script>