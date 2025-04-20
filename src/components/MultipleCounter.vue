<script setup lang="ts">

import { ref } from 'vue';
import CounterStateless from './CounterStateless.vue';

const counter = ref(0)

const increment = () => {
    counter.value++
}

const incrementByValue = (value: number) => {
    counter.value += value
}

</script>

<template>
    <div>
        <CounterStateless :counter="counter" name="Joko" @increment="incrementByValue" />

        <CounterStateless :counter="counter" name="Budi" @increment="incrementByValue" />

        <button @click="increment">Increment</button>
    </div>
</template>


<style scoped>

</style>