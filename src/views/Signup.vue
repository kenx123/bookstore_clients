<template>
  <v-container>
    <v-form>
      <v-text-field v-model="client.name"  label="Name"></v-text-field>
      <v-text-field v-model="client.email" label="Email"></v-text-field>
      <v-text-field v-model="client.phone" label="Phone"></v-text-field>
      <v-text-field v-model="client.address" label="Address"></v-text-field>
      <v-text-field v-model="client.password" label="Password"></v-text-field>
      <v-btn @click="signup">Signup</v-btn>
    </v-form>
  </v-container>
</template>

<script setup>
import {inject, onMounted, ref} from 'vue'

const axios = inject('axios')

const count = ref(0)
const name = ref('')
const client = ref({})
const data = ref([])
  function signup(){
    console.log("Signup click");
    console.log("Name: "+name.value)
    count.value++;
    axios.post('api/public/signup', client.value)
  }

onMounted(()=> {
  axios.get('api/public/clients')
    .then(response=> data.value=response.data)
})
</script>
