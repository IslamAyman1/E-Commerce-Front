<template>
   
   
       <v-layout>
      <!-- start main app bar -->
      <v-app-bar
        color="primary"
        prominent
      >
     <span class="mr-5">Arabic Baba</span>
      <v-text-field
        density="compact"
        variant="solo"
        placeholder="What Are You Looking For"
        append-inner-icon="mdi-magnify"
        single-line
        hide-details
        class="searchField"
        />        
       <v-menu
      transition="slide-x-transition"
    >
      <template v-slot:activator="{ props }">
        <v-btn
           v-bind="props"
           class="ml-5"

        >
          English
        </v-btn>
      </template>

      <v-list>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          
        >
         <v-list-item-title > <NuxtLink class="text-decoration-none" to="#">{{ item.title }}</NuxtLink></v-list-item-title>
        </v-list-item>
      </v-list>
    </v-menu>
     <v-dialog
      v-model="dialog"
      width="400"
      >
      <template v-slot:activator="{ props }">
        <v-btn
           v-bind="props"
           id="mysignin"
           class="signin mr-2" 
        >
        <v-icon class="mr-2">mdi-login</v-icon>  Sign In
        </v-btn>
      </template>

      <v-card>
        <v-card-title class="text-center" >
        <span>Sign In</span> <br/>
         <span class="text-center">Welcome In Your Account</span> <br/>
         <span class="text-center">Dont have an account?
            <v-dialog
        transition="dialog-top-transition"
        width="450"
       >
        <template v-slot:activator="{ props }" >
        <NuxtLink class="text-decoration-none" v-bind=props>Sign Up</NuxtLink>
        </template>
        <template v-slot:default="{ isActive }">
          <v-card>
            <v-toolbar
              color="primary"
              title="Sign Up"
              class="text-center"
            ></v-toolbar>
            <v-card-text class="text-center"> 
              <span class="text-h5"> Create an account</span><br>
               already have an account?<NuxtLink  @click="isActive.value=false" class="text-decoration-none">Sign In</NuxtLink>
             </v-card-text>
             <v-row class="mt-5">
               <v-col  md="12">
                  <v-text-field density="compact" class="ml-4 mr-4" label="Email*" v-model="CreateAccount.email"  required/>
                  <v-text-field density="compact" type="password" class="ml-4 mr-4" v-model="CreateAccount.password" label="Password*" required/>
                  <v-text-field density="compact" class="ml-4 mr-4" label="First Name*" v-model="CreateAccount.firstName" required/>
                  <v-text-field density="compact" class="ml-4 mr-4" label="Last Name*"  v-model="CreateAccount.lastName" required/>

               </v-col>
             </v-row>
            <v-card-actions class="justify-center">
              <NuxtLink class="text-decoration-none text-h6" @click="CheckData()">Create an account</NuxtLink>
              
            </v-card-actions>
            <v-icon class="mdiClose colordifferent" @click="isActive.value=false">mdi-close</v-icon>
          </v-card>
        </template>
      </v-dialog>
         </span>
         <br/>
         <br/> 

        </v-card-title >
         <v-text-field class="ml-5 mr-5" label="Email*" required density="compact" /> 
         <v-text-field class="ml-5 mr-5" label="Password*" required density="compact" />
         <NuxtLink to="#" class="text-center text-decoration-none">Forget Password?</NuxtLink>
         <br/> 
         <hr class="mb-5">
         <NuxtLink to="#" class="text-decoration-none text-center mb-3 text-h6">Sign In</NuxtLink>
         <v-card-actions class="mdiClose ">
         <v-icon @click="dialog=false">mdi-close</v-icon>
        </v-card-actions>
      </v-card>
    </v-dialog>
        <v-icon size="small" class="mr-1">mdi-cart</v-icon>
        <NuxtLink to="mycart" class="mr-5 text-decoration-none text-white" variant="text">Cart</NuxtLink>

      </v-app-bar>
      <!-- end main app bar -->
    
        <!-- start help button -->
        <div class="text-center helpBtn">
          <v-dialog
        transition="dialog-bottom-transition"
        max-width="400"
        
      >
        <template v-slot:activator="{ props }">
          <v-btn
            color="blue-grey-darken-3"
            v-bind="props"
          ><v-icon class="mr-2">mdi-chat</v-icon> Help</v-btn>
        </template>
        <template v-slot:default="{ isActive }">
          <v-card class="mydialog">
            <v-toolbar
              color="primary"
              >
          <v-toolbar-title class="text-center text-h5 mt-9 h-100">
            Help
            </v-toolbar-title>
          </v-toolbar>
            <v-card-text>
              <ul>
                Top Suggestion
                <li><a href="#">What is Arabic Baba return policy?</a></li>

              </ul>
            </v-card-text>
            <v-card-actions class="justify-end">
              <v-icon
                variant="text"
                @click="isActive.value = false"
                class="closeBtnHelp"
              >mdi-close</v-icon>
              <v-btn
      color="blue-grey-darken-4"
       
    >
       Live Chat
      <v-dialog
        v-model="liveChat"
        activator="parent"
        max-width="400"
      >
        <v-card class="mydialog">
          <v-icon @click="liveChat=false">mdi-arrow-left</v-icon>

          <span class="text-center text-h6 mt-4">How We Can Help You</span>
          <v-card-text>
          <v-text-field label="Name" />
          <v-text-field label="Phone Number" />
          <v-text-field label="E-mail" />
          <v-textarea clearable label="Message" variant="outlined"></v-textarea>
          </v-card-text>
          <v-card-actions>
            <v-btn color="blue-grey-darken-4" block>Start Chat</v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-btn>
            </v-card-actions>
          </v-card>
        </template>
      </v-dialog>
        </div>
        <!-- end help button -->
        
      <v-app-bar elevation="0">
 <ul class="d-flex justify-space-between" style="list-style: none;width:100%">
          <li> <NuxtLink to="/" class="text-decoration-none">Home</NuxtLink></li>
          <li> <NuxtLink to="electronics" class="text-decoration-none">Electronics</NuxtLink></li>
          <li> <NuxtLink to="beautyHealth" class="text-decoration-none">Beauty&Health</NuxtLink></li>
          <li> <NuxtLink @click="testLogin" to="sellPage" class="text-decoration-none">Sell On Arabic Baba</NuxtLink></li>  
  </ul>
       </v-app-bar>
 
         <slot />
          
       
           
   </v-layout>
   
</template>
<style scoped>
 .searchField{
   width: 60%;
 }
 .mdiClose{
   position: absolute;
    right:0;
}
.colordifferent{
   color:white;
   margin:9px
}
.signInDialog{
   height: 400px;
}
 .helpBtn{
  position:fixed;
  bottom: 50px;
  right:0;
  z-index: 100000;
 }
 .mydialog{
  position: relative;
  left:570px;
  top:180px;
  height: 400px;
  }
 .closeBtnHelp{
   position:absolute;
   top:0;
   margin:9px;
   color:white
 }
</style>

<script setup>
 import {ref} from "vue"
const CreateAccount = reactive({
  email : null,
  password : null,
  firstName : null,
  lastName : null
})
function CheckData(){
for(const key in CreateAccount) {
 if(!CreateAccount[key]){
   console.log(`the ${key} is Null`)
 } 
}
}
const dialog = ref(false)
const liveChat = ref(false)

const items = ref([{ title: 'Arabic' }])

const Electronics = ref([
{
  Name : "Electronics Conent"
}
])
function testLogin(){
  const mysignin = document.getElementsByClassName("signin")
  if(mysignin[0].classList.contains("signin") == true){
    // window.location.replace("/")
    // alert("You dont have an account")
   // dialog.value = true
   }
}

 
// function getData(){
//   const {data : user} =  useFetch(`https://localhost:7119/api/Author/UpdateUser`,{
//      method : "PUT",
//      body : data.value
//   } 
//   )
//         result.value = user._rawValue
//         console.log(result.value);
// }
 </script>