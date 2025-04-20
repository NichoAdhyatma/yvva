<script lang="ts">
  import { defineComponent } from "vue";
  
  export default defineComponent({
    data() {
      return {
        message: "Hello, Vue Option API with TypeScript!",
        count: 0,
      };
    },
    methods: {
      updateMessage() {
        this.message = "Message updated!";
      },
      increment() {
        this.count++;
      },
    },
  
    watch: {
      message: {
        handler(newVal, oldVal) {
          console.log("Message has been updated from", oldVal, "to", newVal);
        },
        immediate: true,
      },
      count: {
        handler(newVal, oldVal) {
          console.log("Count has been updated from", oldVal, "to", newVal);
        },
        immediate: true,
      },  
      
      
    },
    computed: {
      reversedMessage() {
        return this.message.split("").reverse().join("");
      },
      
      negativeCount() {
        return -this.count;
      },

    },
    created() {
      console.log("Component has been created");
    },
    
    mounted() {
      console.log("Component has been mounted");
    },
    beforeMount() {
      console.log("Component has been beforeMounted");
    },
    beforeCreate() {
      console.log("Component has been beforeCreated");
    },
    beforeUpdate() {
      console.log("Component has been beforeUpdated");
    },
    updated() {
      console.log("Component has been updated");
    },

  });
  </script>


<template>
    <div>
      <h1>Normal : {{ message }}</h1>
      <h1>Reserved : {{ reversedMessage }}</h1>
      <button @click="updateMessage">Update Message</button>

      <button @click="increment">Increment</button>
      <h1>Count : {{ count }}</h1>
      <h1>Negative Count : {{ negativeCount }}</h1>
    </div>
  </template>
  
  
  
  <style scoped>
  h1 {
    color: blue;
  }

  div {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
  </style>
  