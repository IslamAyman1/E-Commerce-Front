<template>
    <div v-for="test in api">
       <div v-for="t in test">
            <h1 class="text-center">{{ t.name }}</h1>
       </div>
    </div>
    <button @click="testPost()">Test Post Request</button>
</template>
<script setup>
import {ref} from "vue"
import axios from "axios";

definePageMeta({
    layout:false
})
const apiObject = ref({
    name : "mohammed",
    email : "is606a@gmail.com",
    password : "123456",
    test:"islamayman"
})
// const {data:count} = useFetch('http://127.0.0.1:8000/api/test')
function testPost(){
    axios.post('http://127.0.0.1:8000/api/admin/login',apiObject.value).then(res=>{
        console.log(res.data);
        localStorage.setItem('Admin Token',res.data.adminToken);
    })
// console.log(count2._rawValue);
}
// const api = ref(count._rawValue)
// console.log(api.value);
</script>