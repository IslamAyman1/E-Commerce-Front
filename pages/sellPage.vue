<template>
  <v-main style="min-height: 100dvh;">
    <v-container>
      <p class="text-h5 text-center">Post Your AD</p>
      <v-card class="mt-4"> 
        <p class="text-h6 ml-4 mt-4">Select Categories</p>
         <v-col>
          <v-select
      :items="items"
      density="compact"
    ></v-select>
         </v-col>
       <p class="text-h6 ml-4">Some Details</p>
       <v-col>
       <p class="ml-2 mt-5">AD Title</p>
       <v-text-field class="mt-5" placeholder="Mention the key features of your item (e.g. brand, model, age, type)"/>
       <p class="ml-2 mt-5">Description</p>
       <v-text-field class="mt-5 desc" style="height:280px" placeholder="Include condition, features and reason for selling"/>
       <hr/>
      </v-col>
      <v-col>
        <p class="text-h5">Set A Price</p>
        <v-text-field type="number" class="mt-5" variant="solo"/>
         <hr/>

        <p class="text-h5 mt-8">Upload Photo</p>
          <v-file-input
          label="Drop Images*"
          variant="filled"
          prepend-icon="mdi-camera"
          accept="image/*"
          show-size
          multiple
          class="mt-6"
         />
      </v-col>
      <hr/>
      <v-col>
         <p class="text-h5 mt-8">Review Your Details</p>
         <p class="mt-7">Name</p>
         <v-text-field class="mt-6" variant="solo" />
         <p class="mt-7">Phone Number</p>
         <v-text-field type="number" class="mt-6" variant="solo" />
      </v-col>
      <v-btn color="primary" class="ml-3 mb-8 mt-4">Post Now</v-btn>
      </v-card>
    </v-container>
  </v-main>
</template>
<script setup>
import {ref} from "vue"
definePageMeta({
    layout : "default"
})
const items = ref(["Car" , "Women" , "Men"])


</script>
<style scoped>

</style>
  <!-- <v-file-input
          label="Drop Images*"
          variant="filled"
          prepend-icon="mdi-camera"
          accept="image/*"
          show-size
          multiple
         ></v-file-input> -->