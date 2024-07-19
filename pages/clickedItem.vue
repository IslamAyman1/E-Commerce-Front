<template>
    <v-main style="min-height: 100dvh;">
        <v-container>
          <v-card class="mt-8">
        <v-row class="mt-5 ml-8 mr-6">
          <v-col md="2" sm="12" class="d-flex flex-column justify-space-between ml-8 ">               
              <img height="100" width="100" src="/Electronics/pexels-cottonbro-studio-5081399.jpg">
              <img height="100" width="100" src="/Electronics/pexels-jess-bailey-designs-788946.jpg">
              <img height="100" width="100" src="/Electronics/pexels-arun-thomas-1156684.jpg">
           </v-col>
        <v-col v-for="(res,index) in result" :key="index"  class="d-flex">
             <v-col md="7">
              <v-img height="400" width="400" :src="res.Img" />
             </v-col>
             <v-col md="4">
              <h4 class="m-3">{{ res.Type }}</h4> <br/>
            <h3 class="m-8">Now:EGP{{ res.price }}</h3>
            <h3 class="mt-8">Order in 15 hrs 16 mins<br/>Free Delivery by Thu, 24 Aug</h3>
            <v-radio-group inline label="Size" class="mt-5">
              <v-radio label="Small" value="1" />
              <v-radio label="Medium" value="2" />
              <v-radio label="Large" value="3" />
            </v-radio-group>
              <v-row>
                  <v-text-field  maxlength=1 label="Quantity" />               
                  <v-btn color="primary" block @click="getcardvalue(res , res.Id)">
                    Add To Cart
                </v-btn>
                <NuxtLink to="/" class="ml-10">
                  <v-btn color="primary" class="mt-4">
                  Continue Shopping
                </v-btn>
                </NuxtLink>
              </v-row>
             </v-col>
         </v-col>
        </v-row>
      </v-card>
    </v-container>
    <v-navigation-drawer
        v-model="drawer"
        temporary
      >
            <div v-for="total,index in cartItem" :key="index">
            <img :src="total.Img" class="mt-4" alt="total image" width="250" height="150">
              <h4 class="text-center mb-4">{{total.name}}</h4>
              <div class="d-flex justify-space-around">
                <v-btn size="x-small" @click="ChangeNumberOfUnit('plus' , total.Id)">+</v-btn>
                <p>{{total.numberOfUnit}}</p>
                <v-btn size="x-small" @click="ChangeNumberOfUnit('minus' , total.Id)">-</v-btn>   
              </div>
              <v-btn block size="small" class="mt-4" color="primary" @click="removeItem(index)">remove</v-btn>
         </div>
      </v-navigation-drawer>
        
    <!-- <myfooter class="foter"/> -->
    </v-main>
</template> 
<script setup>
import {ref , onMounted} from "vue"
definePageMeta({
    layout : "default"
})
     
const result = ref([])
var cartItem = ref([]) 
var check = ref()
  function ReturnFromLocalStorage(){
  result.value.push(JSON.parse(localStorage.getItem("ClickedItem")))
}                   

function getcardvalue(res , id){
  
   cartItem.value =  JSON.parse(localStorage.getItem('myOrders'))
  if(cartItem.value.some((item)=> item.Id == id)){
    drawer.value = true
    ChangeNumberOfUnit('plus' , id)
  }else {
    drawer.value = !drawer.value
    cartItem.value.push({...res , numberOfUnit : 1})
    //  console.log(id);
  }
    localStorage.setItem("myOrders" , JSON.stringify(cartItem.value)) 
  
  }

 
function ChangeNumberOfUnit(action , Id){
    cartItem.value = cartItem.value.map((item) => {
    let numberOfUnit = item.numberOfUnit
    if (item.Id === Id){
      if (action == 'minus' && numberOfUnit > 1) {
        numberOfUnit--;

      } else if (action == 'plus' && numberOfUnit < item.stock) {
        numberOfUnit++;

      }
    }
  
    return {
      ...item,
      numberOfUnit,
    };

  })
  localStorage.setItem("myOrders" , JSON.stringify(cartItem.value)) 
}
function removeItem(index){
   cartItem.value.splice(index , 1)
  localStorage.setItem("myOrders" , JSON.stringify(cartItem.value))
 }
 onMounted(()=>{
   ReturnFromLocalStorage() 

})
const drawer = ref(null)
</script>
<style>
 .foter{
  position: absolute;
  bottom: 0;
 }
</style>