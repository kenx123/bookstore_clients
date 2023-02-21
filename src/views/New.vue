<template>
  <v-container>
    <v-form>
      <v-text-field v-model="client.name"  label="Name"></v-text-field>
      <v-text-field v-model="client.email" label="Email"></v-text-field>
      <v-text-field v-model="client.phone" label="Phone"></v-text-field>
      <v-text-field v-model="client.address" label="Address"></v-text-field>
      <v-btn @click="save">Save</v-btn>
      <v-btn @click="getClients">GetClients</v-btn>
      <v-btn @click="getClient">GetClient</v-btn>
    </v-form>
    <v-col
      cols="12"
      sm="6"
    >
      <v-text-field
        value=response.data
        label="Solo"
        solo
        readonly
      ></v-text-field>
    </v-col>
  </v-container>
</template>

<script setup>
import {inject, onMounted, ref} from 'vue'

const axios = inject('axios')

const count = ref(0)
const name = ref('')
const client = ref({})
const data = ref([])
  function save(){
    console.log("Save click");
    console.log("Name: "+name.value)
    count.value++;
    axios.post('api/client', client.value)
  }
  function getClients(){
    console.log("GetClients click");
    axios.get('api/clients')
  }

function getClient(){
  console.log("GetClient click");
  name.value = 'Madis Karja';
  axios.get('api/client/'+name.value)
}

onMounted(()=> {
  axios.get('api/clients')
    .then(response=> data.value=response.data)
})
</script>
