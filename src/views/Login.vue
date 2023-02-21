<template>
  <v-container>
    <v-form>
      <v-text-field v-model="client.email" label="Email"></v-text-field>
      <v-text-field v-model="client.password" label="Password" type="password"></v-text-field>
      <v-btn @click="login">Login</v-btn>
    </v-form>
    <v-table>
      <thead>
      <th>JWT</th>
      </thead>
      <tbody>
      <tr v-for="item in data" :key="item.id">
        <td>{{item.name}}</td>
      </tr>
      </tbody>
    </v-table>
  </v-container>
</template>

<script setup>
import {inject, onMounted, ref} from 'vue'

const axios = inject('axios')


const client = ref({})
const data = ref([])

function login(){
  axios.post('api/public/login', client)
    .then(response => {
      axios.defaults.headers.common['Authorization'] =  "Bearer " + response.data.token
      localStorage.setItem("token", response.data.token)
    })
    .catch(response => { response.response.data})
}

</script>
