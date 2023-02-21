<template>
  <v-app-bar flat>
    <v-app-bar-title>
      <v-icon icon="mdi-circle-slice-4" />
      Bookstore
      <v-btn>
        <router-link to="/">Home</router-link>
      </v-btn>
      <v-btn>
        <router-link to="/new">New</router-link>
      </v-btn>
      <v-btn>
        <router-link to="/login">Login</router-link>
      </v-btn>
    </v-app-bar-title>
  </v-app-bar>
</template>

<script setup>
  //
</script>
