<template>
      <v-carousel
    progress="primary"
  >
    <v-carousel-item
      v-for="(slide, i) in data"
      :key="i"
      :src="slide"  cover  >
    </v-carousel-item>
  </v-carousel>
</template>
<script setup>
defineProps({
    data : { 
        type: Array 
 }
})
 
</script>
