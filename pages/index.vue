<template>
<v-main>
  <carousal :data="slides" />
  <slidegroup :slideItem="selectedItem" />
    
     <!--start 8 card -->
      <eightCard :data="ElectronicCard" />
     <!--end 8 card  -->

 <!-- start card with hover -->
  <p class="text-center text-h4 mt-12">Beauty&Health</p>
  <v-row class="mt-8">
    <v-col cols="12" md="3" sm="12" 
     v-for="hover,index in HoverCard"
     :key="index"
    >
      <v-hover v-slot="{ isHovering, props }">
      <v-card
        class="mx-auto"
        color="grey-lighten-4"
        max-width="600"
        v-bind="props"
      >
        <NuxtLink to="clickedItem" @click="EnterPage(hover)">
          <v-img  
          :aspect-ratio="16/9"
          cover
          :src="hover.Img"
        >
          <v-expand-transition>
            <div
              v-if="isHovering"
              class="d-flex transition-fast-in-fast-out bg-purple-darken-3 v-card--reveal text-h2"
              style="height: 100%;"
            >
              {{ hover.price }}
            </div>
          </v-expand-transition>
        </v-img>
      </NuxtLink>

        <v-card-text class="pt-6">
          <div class="font-weight-light text-grey text-h6 mb-2">
            {{ hover.Name }}
          </div>

          <h3 class="text-h5 font-weight-light text-orange mb-2">
            {{ hover.Type }}
          </h3>

          <div class="font-weight-light text-h6 mb-2">
            {{ hover.Description }}
          </div>
        </v-card-text>
      </v-card>
    </v-hover>
    </v-col>
  </v-row>
 <!-- end card with hover -->
 
    <!--start 8 card -->
    <p class="text-center text-h4 mt-12">Baby And Toys</p>
    <eightCard :data="BabyToysCards" />
     <!--end 8 card  -->


    
    
 
  

<!-- <div class="text-h4 text-center mt-9">Shop Other Categories</div>

  <v-row class="mt-5">
      <v-col
        v-for="n in 4"
        :key="n"
        class="d-flex child-flex"
        cols="3"
      >
        <v-img
          :src="`https://picsum.photos/500/300?image={n * 5 + 10}`"
          aspect-ratio="15/2"
          cover
          class="bg-grey-lighten-2"
        >
          <template v-slot:placeholder>
            <v-row
              class="fill-height ma-0"
              align="center"
              justify="center"
            >
              <v-progress-circular
                indeterminate
                color="grey-lighten-5"
              ></v-progress-circular>
            </v-row>
          </template>
        </v-img>
      </v-col>
    </v-row> -->

  <!-- <myfooter /> -->
</v-main>  
  
</template>

  
<script setup>
import {ref} from "vue"

 definePageMeta({
  layout : "default"
})
     const selectedItem = ref(
      [
      {
        Id : 1,
        name : "First Electronic",
        Img: "/Electronics/download (1).jpeg",
        Type : "Electronic",
        price : 25.00,
        stock : "5",
      },
      {
        Id :2,
        name : "second Electronic",
        Img: "/Electronics/download.jpeg",
        Type : "Electronic",
        price : 15.00,
        stock : "5",
      },
      {
        Id :3,
        name : "third Electronic",
        Type : "Electronic",
        Img : "/Electronics/images (1).jpeg",
        price : 9.50,
        stock : "5",
      },
      {
        Id :4,
        name : "fourth Electronic",
        Type : "Electronic",
        Img : "/Electronics/images (2).jpeg",
        price : 31.50,
        stock : "5",
      },
      {
        Id :5,
        name : "fifth Electronic",
        Type : "Electronic",
        Img : "/Electronics/images (3).jpeg",
        price : 7.50,
        stock : "5",
      },
      {
        Id :6, 
        name : "Six Electronic",
        Type : "Electronic",
        Img : "/Electronics/images.jpeg",
        price : 43.00,
        stock : "5"
      }
    ]
    )
    const ElectronicCard = ref([
      {
        Id : 7,
        name : "Readme",
        Description : "New Electronic device!!",
        Type : "Phone",
        Img : "/Electronics/download (1).jpeg",
        price : 25.00,
        stock : "5"
      },
      {
        Id : 8,
        name : "Realme",
        Description : "New Electronic device!!",
        Type : "Phone",
        Img : "/Electronics/download.jpeg",
        price : 18.00,
        stock : "5"
      },
      {
        Id : 9,
        name : "IPhone",
        Description : "New Electronic device!!",
        Type : "Phone",
        Img: "/Electronics/images (1).jpeg",
        price : 31.00,
        stock : "5"
      },
      {
        Id : 10,
        name : "Samsung",
        Description : "New Electronic device!!",
        Type : "Phone",
        Img : "/Electronics/images (2).jpeg",
        price : 18.00,
        stock : "5"
      },
      {
        Id : 11,
        name : "Galaxy",
        Description : "New Electronic device!!",
        Type : "Phone",
        Img : "/Electronics/images (3).jpeg",
        price : 12.75,
        stock : "5"
      },
      {
        Id : 12,
        name : "IPhone",
        Description : "New Electronic device!!",
        Type : "Phone",
        Img : "/Electronics/images.jpeg",
        price : 11.00,
        stock : "5"
      },
      {
        Id : 13,
        name : "Chaomi",
        Description : "New Electronic device!!",
        Type : "Phone",
        Img : "/Electronics/pexels-antonio-borriello-1297611.jpg",
        price : 35.00,
        stock : "5"
      },
      {
        Id : 14,
        name : "IPhone",
        Description : "New Electronic device!!",
        Type : "Phone",
        Img : "/Electronics/pexels-arun-thomas-1156684.jpg",
        price : 10.50,
        stock : "5"
      }
    ])
    const HoverCard = ref([
      {
       Id : 15,
       name : "Fuck",
       Description : "New Beauty&Health Product",
       Type : "Beauty&Health",
       Img : "/Beauty&Health/pexels-arina-krasnikova-6664045.jpg",
       price : 10.00,
       stock : "5"
    },
    {
       Id : 16,
       name : "Bodra",
       Description : "New Beauty&Health Product",
       Type : "Beauty&Health",
       Img : "/Beauty&Health/pexels-cottonbro-studio-3737560.jpg",
       price : 14.00,
       stock : "5"
    },
    {
       Id : 17,
       name : "Wow",
       Description : "New Beauty&Health Product",
       Type : "Beauty&Health",
       Img : "/Beauty&Health/pexels-karolina-grabowska-4202325 (2).jpg",
       price : 11.50,
       stock : "5"
    },
    {
       Id : 18,
       name : "Leb",
       Description : "New Beauty&Health Product",
       Type : "Beauty&Health",
       Img : "/Beauty&Health/pexels-karolina-grabowska-4938502.jpg",
       price : 13.50,
       stock : "5"
    },
    {
       Id : 19,
       name : "Glas",
       Description : "New Beauty&Health Product",
       Type : "Beauty&Health",
       Img : "/Beauty&Health/pexels-natalia-hawthorne-3785147.jpg",
       price : 9.50,
       stock : "5"
    },
    {
       Id : 20,
       name : "Maskara",
       Description : "New Beauty&Health Product",
       Type : "Beauty&Health",
       Img : "/Beauty&Health/pexels-suzy-hazelwood-1327689 (1).jpg",
       price : 7.00,
       stock : "5"
    },
    {
       Id : 21,
       name : "Blashr",
       Description : "New Beauty&Health Product",
       Type : "Beauty&Health",
       Img : "/Beauty&Health/pexels-𝐕𝐞𝐧𝐮𝐬-𝐇𝐃-𝐌𝐚𝐤𝐞-𝐮𝐩-&-𝐏𝐞𝐫𝐟𝐮𝐦𝐞-2688991.jpg",
       price : 6.50,
       stock : "5" 
    },
    {
       Id : 22,
       name : "Blashr",
       Description : "New Beauty&Health Product",
       Type : "Beauty&Health",
       Img : "/Beauty&Health/pexels-𝐕𝐞𝐧𝐮𝐬-𝐇𝐃-𝐌𝐚𝐤𝐞-𝐮𝐩-&-𝐏𝐞𝐫𝐟𝐮𝐦𝐞-1749452.jpg",
       price : 22.50,
       stock : "5"
    }])
    const BabyToysCards = ref([
    {
       Id : 23,
       name : "Baby&Toys",
       Description : "New Baby&Toys Product",
       Type : "Baby&Toys",
       Img : "/Baby&Toys/pexels-anna-shvets-3845492.jpg",
       price : 10.00,
       stock : "5"
    },
    {
       Id : 24,
       name : "Baby&Toys",
       Description : "New Baby&Toys Product",
       Type : "Baby&Toys",
       Img : "/Baby&Toys/pexels-cottonbro-studio-3661389.jpg",
       price : 14.00,
       stock : "5"
    },
    {
       Id : 25,
       name : "Baby&Toys",
       Description : "New Baby&Toys Product",
       Type : "Baby&Toys",
       Img : "/Baby&Toys/pexels-emily-ranquist-1205650.jpg",
       price : 11.50,
       stock : "5"
    },
    {
       Id : 26,
       name : "Baby&Toys",
       Description : "New Baby&Toys Product",
       Type : "Baby&Toys",
       Img : "/Baby&Toys/pexels-hồng-xuân-viên-2869318.jpg",
       price : 13.50,
       stock : "5"
    },
    {
       Id : 27,
       name : "Baby&Toys",
       Description : "New Baby&Toys Product",
       Type : "Baby&Toys",
       Img : "/Baby&Toys/pexels-markus-spiske-298825.jpg",
       price : 9.50,
       stock : "5"
    },
    {
       Id : 28,
       name : "Baby&Toys",
       Description : "New Baby&Toys Product",
       Type : "Baby&Toys",
       Img : "/Baby&Toys/pexels-stas-knop-1330638.jpg",
       price : 7.00,
       stock : "5"
    },
    {
       Id : 29,
       name : "Baby&Toys",
       Description : "New Baby&Toys Product",
       Type : "Baby&Toys",
       Img : "/Baby&Toys/pexels-pixabay-459976.jpg",
       price : 6.50,
       stock : "5" 
    },
    {
       Id : 30,
       name : "Baby&Toys",
       Description : "New Baby&Toys Product",
       Type : "Baby&Toys",
       Img : "/Baby&Toys/pexels-pixabay-266004.jpg",
       price : 22.50,
       stock : "5"
    }
    ])
    function EnterPage(item){
     localStorage.setItem("ClickedItem", JSON.stringify(item))
}
   

   const slides = ref(['/Electronics/pexels-cottonbro-studio-5081399.jpg' ,
    '/Beauty&Health/pexels-cottonbro-studio-3737560.jpg' ,
    '/Beauty&Health/pexels-𝐕𝐞𝐧𝐮𝐬-𝐇𝐃-𝐌𝐚𝐤𝐞-𝐮𝐩-&-𝐏𝐞𝐫𝐟𝐮𝐦𝐞-2688991.jpg'])
     

     const tab = ref(null)
  
</script>

<style scoped>
 .v-card--reveal {
    align-items: center;
    bottom: 0;
    justify-content: center;
    opacity: .9;
    position: absolute;
    width: 100%;
  }
</style>  