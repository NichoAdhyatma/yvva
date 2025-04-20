<script setup lang="ts">

const product = defineProps({
    id: {
        type: Number,
        required: true
    },
    name: {
        type: String,
        required: true,
        validator(value: string) {
            return value.length > 0
        }
    },
    price: {
        type: Number,
        required: true,
        validator(value: number) {
            return value > 0
        }
    }
});

</script>

<template>
    <div>
        <h2>{{ product.name }}</h2>
        <p>ID: {{ product.id }}</p>
        <p>Price: ${{ product.price }}</p>  
    </div>
</template>


<style scoped>
div {
    border: 1px solid #ccc;
    padding: 10px;
    border-radius: 5px;
}
</style>