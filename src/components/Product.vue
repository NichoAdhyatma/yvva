<script setup lang="ts">
import { computed, onMounted, onWatcherCleanup, ref, watchEffect } from 'vue';


type Product = {

    id: number
    name: string
    price: number
    description: string
    image: string
}

const selectedId = ref(1)

const products = ref<Product[]>([])

const timer = ref(5)

const selectedProduct = computed<Product | undefined>(() => {
    console.log("Selected Product is called")
    
    return products.value.find((product) => product.id === selectedId.value)
})


// watch([selectedId, selectedProduct], async (value, oldValue, onCleanup) => {
//     console.log(value, oldValue)

//     if (value[1]) {
//         switch (value[1].id) {
//             case 1:
//                 value[1].image = "https://loremflickr.com/320/240"
//                 break
//             case 2:
//                 value[1].image = "https://loremflickr.com/g/320/240/paris"
//                 break
//             case 3:
//                 value[1].image = "https://loremflickr.com/g/320/240/paris,girl/all"
//                 break
//         }
//     }


//     onCleanup(() => {
//         console.log('cleanup')
//     })
// }, {immediate: true})

watchEffect((onCleanup) => {
    console.log("watchEffect is called")

    if (selectedProduct.value) {
        switch (selectedProduct.value.id) {
            case 1:
                selectedProduct.value.image = "https://loremflickr.com/320/240"
                break
            case 2:
                selectedProduct.value.image = "https://loremflickr.com/g/320/240/paris"
                break
            case 3:
                selectedProduct.value.image = "https://loremflickr.com/g/320/240/paris,girl/all"
                break
        }
    }

    onWatcherCleanup(() => {
        console.log("onWatcherCleanup is called")
    })

    onCleanup(() => {
        console.log("onCleanup is called")
    })
})

const timerInterval = setInterval(() => {
    timer.value--
}, 1000)

 onMounted(async () => {
    const response = await fetch(`/products.json`)

    const data = await response.json()

    products.value = data.data
})

const clearTimer = watchEffect(() => {
    if(timer.value === 0) {
        console.log("timer is 0")

        clearInterval(timerInterval)

        clearTimer()
    
    }

    console.log("run once")  
})
</script>


<template>
    <div>
        <h1>Product</h1>

        {{ timer }}

        <div>
            <select v-model="selectedId">
                <option v-for="product in products" :key="product.id" :value="product.id">
                    {{ product.name }}
                </option>
            </select>

            <button @click="timer--">Change Product</button>
        </div>

        <div>
            <h2>{{ selectedProduct?.name }}</h2>
            <p>{{ selectedProduct?.description }}</p>
            <p>{{ selectedProduct?.price }}</p>
            <img :src="selectedProduct?.image" alt="Product Image">
        </div>
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