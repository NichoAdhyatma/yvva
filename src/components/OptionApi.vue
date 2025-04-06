<script lang="ts">
  import { defineComponent } from "vue";
  
  export default defineComponent({
    data() {
      return {
        message: "Hello, Vue Option API with TypeScript!",
      };
    },
    methods: {
      updateMessage() {
        this.message = "Message updated!";
      },
    },
    created() {
      console.log("Component has been created");
    },
    computed: {
      reversedMessage() {
        return this.message.split("").reverse().join("");
      },
    },
  });
  </script>


<template>
    <div>
      <h1>Normal : {{ message }}</h1>
      <h1>Reserved : {{ reversedMessage }}</h1>
      <button @click="updateMessage">Update Message</button>
    </div>
  </template>
  
  
  
  <style scoped>
  h1 {
    color: blue;
  }
  </style>
  