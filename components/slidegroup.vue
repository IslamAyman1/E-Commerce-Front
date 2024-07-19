<template>
      <v-sheet
    class="mx-auto"
    elevation="8"
   >
    <v-slide-group
      v-model="model"
      class="pa-4"
      selected-class="bg-primary"
      show-arrows
    >
      <v-slide-group-item
        v-for="item , index in slideItem"
        :key="index">
         
         <v-card class="mx-auto my-12 ml-9"   elevation="0">
             <NuxtLink to="clickedItem" @click="EnterPage(item)">
              <v-img
             contain     
             height="250"
             width="250"
             :src="item.Img"
           />
          </NuxtLink>
          <h4 class="text-center">{{ item.name }}</h4>
         </v-card>
      </v-slide-group-item>
    </v-slide-group>

    <v-expand-transition>
      <v-sheet
        v-if="model != null"
        height="200"
      >
        <div class="d-flex fill-height align-center justify-center">
          <h3 class="text-h6">
             {{ slideItem[model].Id }}
             {{ slideItem[model].name }}

          </h3>
        </div>
      </v-sheet>
    </v-expand-transition>
  </v-sheet>
</template>
<script setup>
import {ref} from "vue"
const model = ref(null)
defineProps({
  slideItem : {
    type : Array
  }
})
function EnterPage(item){
 localStorage.setItem("ClickedItem", JSON.stringify(item))
}
</script>
