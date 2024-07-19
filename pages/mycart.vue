<template >
         
    <v-main style="min-height: 100dvh;">
             <v-container >
                 <!-- <h3 class="">Cart <sub>(item {{cartItem.value.length}})</sub></h3> -->
                 <v-row>
                     <v-col md="8" style="overflow: auto; height: 480px;">
                        <p class="mt-4 text-center">The prices of some products in your cart have changed <br>Please review your cart before proceeding</p>
                     <div  v-for="mycart , index in cartItem"  :key="index ">
                        <v-card class="w-100 d-flex justify-space-around mt-5">
                     <div>
                        <img width="200" height="200" :src="mycart.Img" alt="Product Image">
                     </div>
                    <div class="mt-4">
                        <h3>{{ mycart.name }}</h3><br> 
                    <h3> Product Price : {{ mycart.price }}</h3><br>
                    <h3> Product Count : {{ mycart.numberOfUnit }}</h3>
                    <v-btn class="mt-5" color="primary" @click="RemoveFromCart(index)">Remove</v-btn>
                    </div>
                </v-card>
            </div>  
                <hr>
                 </v-col>
                 <v-col class="mt-13">
                         <h3 class="text-center">CheckOut</h3>
                     <div class="d-flex justify-space-between mt-5">
                        <h3>SubTotal <sub>(items {{ TotalItem }})</sub></h3> 
                         <h3> {{ TotalPrice }} EGP</h3>
                        </div>
                       <div class="d-flex justify-space-between mt-5">
                        <h4>Shipping Details</h4>
                        <h4 class="text-blue">Free</h4>
                       
                       </div>
                       <hr class="mt-9">
                       <div class="mt-5 d-flex justify-space-between">
                         <h3>Total</h3>
                         <h3>{{ TotalPrice }} EGP</h3>
                       </div>
                       <hr class="mt-7">
     <v-dialog v-model="dialog" persistent width="500">
      <template v-slot:activator="{ props }">
        <v-btn
          color="primary"
          class="mt-8"
          v-bind="props"
          block
        >
         CheckOut
        </v-btn>
      </template>
      <v-card>
        <v-card-title class="text-h5 text-center">
          New Address Details!!
        </v-card-title>
        <!-- <v-card-text>Location Information</v-card-text> -->
          
        <v-text-field class="ma-8" label="Additional Address Details *" hint="This should start with a letter, but you can add a number after" density="compact" placeholder="Building no,Floor no,Flat no" />
         <hr>
           <v-text-field density="compact" label="Mobile Number *" type="Number"  class="ma-8" />
           <h3 class="text-center">Personal Information</h3>
            <v-row class="mt-4">
                <v-text-field label="First Name *" density="compact" class="mr-2" />
                <v-text-field label="Last Name *" density="compact" />
            </v-row>
           <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="green-darken-1"
            variant="text"
            block
            @click="dialog = false"
          >
            Confirm
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
                  </v-col>
                 </v-row>
             </v-container>
            <!-- <myfooter class="myfoter"/> -->
     </v-main>
        
 </template>
<script setup>
import {ref , onMounted} from "vue"
definePageMeta({
    layout : "default"
})
const cartItem = ref([])
const TotalPrice = ref(0)
const TotalItem = ref(0)
const dialog = ref(false)
function ReturnFromLocalStorage(){
    cartItem.value = JSON.parse(localStorage.getItem('myOrders'))
}
function renderTotalPrice(){
    cartItem.value = JSON.parse(localStorage.getItem("myOrders"))
    cartItem.value?.forEach((items)=>{
      TotalPrice.value += items.price * items.numberOfUnit
      TotalItem.value += items.numberOfUnit 
    })
    localStorage.setItem("myOrders" , JSON.stringify(cartItem.value))


    console.log(TotalPrice.value);
}
function RemoveFromCart(index){
cartItem.value.splice(index , 1)
localStorage.setItem("myOrders" , JSON.stringify(cartItem.value))
location.reload()
}
 onMounted(()=>{
    ReturnFromLocalStorage()
    renderTotalPrice()
 })
</script>
<style scoped>
.image{
    height:300px;
    width:300px;
    margin-bottom: 9px;
    position:relative;
    left:38%;
    top:60px
 }
 .myfoter{
    position: absolute;
    bottom:0;
 }
</style>