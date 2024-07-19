<template>
    <v-main style="min-height: 100dvh;">
        <carousal :data= beautyArray />
         <slidegroup :slideItem=selectedItem />
    </v-main>
</template>
<script setup>
  import {ref} from "vue"
definePageMeta({
    layout : "default"
})
const beautyArray = ref(["/Beauty&Health/pexels-karolina-grabowska-4202325 (2).jpg" , "/Beauty&Health/pexels-karolina-grabowska-4938502.jpg" , "/Beauty&Health/pexels-suzy-hazelwood-1327689 (1).jpg"])
const selectedItem = ref(
      [
      {
        Id : 1,
        name : "First Electronic",
        Img: "/Beauty&Health/pexels-arina-krasnikova-6664045.jpg",
        Type : "Electronic",
        price : "25.00$",
        stock : "5"
      },
      {
        Id :2,
        name : "second Electronic",
        Img: "/Beauty&Health/pexels-cottonbro-studio-3737560.jpg",
        Type : "Electronic",
        price : "15.00$",
        stock : "5"

      },
      {
        Id :3,
        name : "third Electronic",
        Type : "Electronic",
        Img : "/Beauty&Health/pexels-karolina-grabowska-4202325 (2).jpg",
        price : "9.50$",
        stock : "5"
      },
      {
        Id :4,
        name : "fourth Electronic",
        Type : "Electronic",
        Img : "/Beauty&Health/pexels-karolina-grabowska-4938502.jpg",
        price : "31.50$",
        stock : "5"

      },
      {
        Id :5,
        name : "fifth Electronic",
        Type : "Electronic",
        Img : "/Beauty&Health/pexels-natalia-hawthorne-3785147.jpg",
        price : "7.50$",
        stock : "5"
      },
      {
        Id :6, 
        name : "Six Electronic",
        Type : "Electronic",
        Img : "/Beauty&Health/pexels-suzy-hazelwood-1327689 (1).jpg",
        price : "43.00$",
        stock : "5"
      },
      {
        Id :7, 
        name : "Seven Electronic",
        Type : "Electronic",
        Img : "/Beauty&Health/pexels-𝐕𝐞𝐧𝐮𝐬-𝐇𝐃-𝐌𝐚𝐤𝐞-𝐮𝐩-&-𝐏𝐞𝐫𝐟𝐮𝐦𝐞-1749452.jpg",
        price : "43.00$",
        stock : "5"
      }
    ]
    )
</script>
<style scoped>

</style>