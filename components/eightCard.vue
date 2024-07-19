  <template>
      <v-row class="mt-8">

        <v-col cols="12" md="3" sm="12"  
      v-for="electron , index in data"
      :key="index" >
          
        <v-card max-width="374">
        <NuxtLink to="clickedItem" @click="EnterPage(electron)">
        <v-img
        cover
        height="250"
        :src="electron.Img"
      ></v-img>
      </NuxtLink>
      <v-card-item>
        <v-card-title>{{ electron.name }}</v-card-title>

        <v-card-subtitle>
          <span class="text-center">{{ electron.Description }}</span>
        </v-card-subtitle>
      </v-card-item>
        </v-card>
        </v-col>
        
      </v-row>
  </template>
<script setup>
   defineProps({
     data : {
        type : Array
     }
   })
 function EnterPage(item){
 localStorage.setItem("ClickedItem", JSON.stringify(item))
}
</script>