<template>
  <div class="container">
    <h1>New Contact</h1>
    <div>
      First name: <input type="text" v-model="newContctFirstName">
      Middle name: <input type="text" v-model="newContctMiddleName">
      Last name: <input type="text" v-model="newContctLastName">
      Phone Number: <input type="text" v-model="newContctPhoneNumber">
      Email: <input type="text" v-model="newContctEmail">
      Company: <input type="text" v-model="newContctContact">
      Bio: <input type="text" v-model="newContctBio">
      <button v-on:click="createContact()">Create Contact</button>
    <h1> All Contacts</h1>
    <div v-for="contact in contacts">
        <h2> {{contact.name}}</h2>
        <!-- <img v-bind src="contact.url">  -->
        <p>first_name:  {{contact.first_name}}</p>
        <p>middle_name: {{contact.middle_name}}</p>
        <p>last_name: {{contact.last_name}}</p>
        <p>phone_number: {{contact.phone_number}}</p>
        <p>email: {{contact.email}}</p>
        <p>company: {{contact.company}}</p>
        <p>bio: {{contact.bio}}</p>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      contacts:[]
    };
  },
  created: function() {
    axios.get("/api/contacts").then(response => {
      this.contacts = response.data;
    });
  },
  methods: {}
};
</script>
