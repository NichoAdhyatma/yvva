<script setup lang="ts">
import { ref } from 'vue';
import About from './About.vue';
import Home from './Home.vue';
import ContactUs from './ContactUs.vue';



const currentPage = ref('About')

const pages = {
    Home,
    About,
    ContactUs
}
        
</script>
<template>
    <div>
        <button @click="currentPage = 'Home'">Home</button>
        <button @click="currentPage = 'About'">About</button>
        <button @click="currentPage = 'ContactUs'">ContactUs</button>
    </div>
    
    <div>
        <component :is="pages[currentPage as keyof typeof pages]" />
    </div>
</template>

<style scoped>

</style>