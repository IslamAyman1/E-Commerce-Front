<template>
  <v-main>
    <carousal :data = slides />
    <slidegroup :slideItem = selectedItems />
  <!-- <myfooter /> -->
  </v-main>  
</template>
<script setup>
import {ref} from "vue"
definePageMeta({
    layout : "default"
})
const slides = ref(['/Electronics/pexels-antonio-borriello-1297611.jpg' , '/Electronics/pexels-polina-zimmerman-3747142.jpg','/Electronics/pexels-cottonbro-studio-5081399.jpg' , '/Electronics/pexels-irina-iriser-1647976.jpg','/Electronics/pexels-jess-bailey-designs-788946.jpg'])
const selectedItems = ref(
      [
      {
        Id : 31,
        name : "Samsung Phon",
        Img: "/Electronics/pexels-vlad-chețan-3121979.jpg",
        Type : "Electronic",
        price : 25.00,
        stock : "5"
      },
      {
        Id :32,
        name : "IPhone",
        Img: "/Electronics/pexels-soulful-pizza-6941486.jpg",
        Type : "Electronic",
        price : 15.00,
        stock : "5"

      },
      {
        Id :33,
        name : "Huwawi Phone",
        Type : "Electronic",
        Img : "/Electronics/pexels-polina-zimmerman-3747142.jpg",
        price : 9.50,
        stock : "5"
      },
      {
        Id :34,
        name : "Oppo Phone",
        Type : "Electronic",
        Img : "/Electronics/pexels-noah-erickson-404280.jpg",
        price : 31.50,
        stock : "5"

      },
      {
        Id :35,
        name : "IPhone Pro",
        Type : "Electronic",
        Img : "/Electronics/pexels-jess-bailey-designs-788946.jpg",
        price : 7.50,
        stock : "5"
      },
      {
        Id :36, 
        name : "DG Filo",
        Type : "Electronic",
        Img : "/Electronics/images (3).jpeg",
        price : 43.00,
        stock : "5"
      },
      {
        Id :37, 
        name : "Labtob",
        Type : "Electronic",
        Img : "/Electronics/images (1).jpeg",
        price : 43.00,
        stock : "5"
      }
    ]
    )
</script>
<style scoped>

</style>