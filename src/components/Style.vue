<script setup lang="ts">
import { reactive } from 'vue';


const classData = reactive({
    red: true,
    bold: false
})

const toggleRed = () => {
    classData.red = !classData.red
}

const toggleBold = () => {
    classData.bold = !classData.bold
}
</script>

<template>

    <p :class="{red: classData.red, bold: classData.bold}">Style</p>

    <p :class="['red', 'bold']">Style</p>

    <p :class="classData">Style</p>

    <button @click="toggleRed">Toggle Red</button>
    <button @click="toggleBold">Toggle Bold</button>
    
</template>



<style scoped>

.red {
    color: red;
}

.bold {
    font-weight: bold;
    text-transform: uppercase;
}
</style>