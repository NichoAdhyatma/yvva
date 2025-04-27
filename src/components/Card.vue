<script setup lang="ts">
import { ref, } from 'vue';


    const counter = ref(0)
</script>
<template>
    <div class="card">
        <div v-if="$slots.header">
            <slot name="header" :counter="counter" />
        </div>
      
        <div v-if="$slots.content" class="card-content">
            <slot name="content" :counter="counter"/>
        </div>

        <slot name="footer" :counter="counter"/>
        
        <button @click="counter++">Increment</button>
    </div>
</template>


<style scoped>
.card {
    border: 1px solid #000;
    padding: 10px;
    border-radius: 5px;
  ;
}

h1 {
    font-size: 20px;
    font-weight: bold;

}

.card-content {
    border: 1px solid #000;
    padding: 10px;
    border-radius: 5px;
}


</style>