<script setup lang="ts">

type CounterStatelessProps = {
    counter: number;
    name: string;
   
}

type CounterStatelessEmits = {
    increment: [value: number]
}

const {counter, name} = defineProps<CounterStatelessProps>();

const emit = defineEmits<CounterStatelessEmits>();

const increment = () => {
    emit('increment', counter);
}

</script>

<template>
    <div>
        <h1>Counter Stateless</h1>

        <h1>{{ name }}</h1>
        <h2>{{ counter }}</h2>

        <button @click="increment">Increment</button>
    </div>
</template>


<style scoped>

div {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}

</style>