<script setup>
const props = defineProps({
    details: {
        // prop validation
        type: Array,
        required: true
    }
});


</script>

<template>
    <ul>
        <li v-for="detail in details">{{ detail }}</li>
    </ul>

</template>