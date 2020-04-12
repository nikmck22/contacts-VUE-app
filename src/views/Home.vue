<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <p>First Name: <input type="text" v-model="newContactFirstName"></p>
    <button v-on:click="addContact()">Add a new contact</button>    
    <div v-bind:key="contact.id" v-for="contact in contacts">
    <p>{{ contact.id }} - {{ contact.first_name }} {{ contact.last_name }}</p>
    <p>{{ contact.email }}</p>
    <p>{{ contact.phone }}</p>
    </div>
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
      sample: "Let's change some text",
      contacts: [],
      newContactFirstName: "",
      newContactLastName: "",
      newContactEmail: "",
      newContactPhoneNumber: ""

    };
  },
  
  created: function() {
    axios.get("/api/contacts").then(response => {
      console.log('Lets show some data');
      this.contacts = response.data;
    });
  },
  methods: {
    addContact: function() {
      console.log('Here is the new contact');
      var params = {
        input_first: this.newContactFirstName,
        input_last: this.newContactLastName,
        input_email: this.newContactEmail,
        input_phone_number: this.newContactPhoneNumber
      };
    }
  }
};
</script>

