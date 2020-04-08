<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <p>{{ sample }}</p>
    <!-- <div v-bind:key="contact.id" v-for="contact in contacts"></div>
    <p>{{ contact.first_name }}</p> -->
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      message: "Welcome to Vue.js!",
      sample: "Here is this working",
      contacts: []

    };
  },
  
  created: function() {
    axios.get("/api/contacts").then(response => {
      console.log('response.data')
    });
  },
  methods: {
   
  }
};
</script>