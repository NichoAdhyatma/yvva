<script setup lang="ts">
import { computed, reactive, ref } from 'vue'


const data = reactive({
    name: '',
    age: '',
})

const handleInput = (event: Event) => {
    const input = event.target as HTMLInputElement

    data[input.name as keyof typeof data] = input.value

    console.log(data)
}


const displayData = computed( () => {
    console.log('displayData is called')

    return `display data ${data.name}`
})

const count = ref(0)

const increment = () => {
    console.log('increment is called')
    
    count.value++
}


</script>

<template>
   
   <button @click="increment">Count is {{ count }}</button>

    <div>
        <input type="text" name="name" id="name" placeholder="Name" @input="handleInput" />

        <input type="text" name="age" id="age" placeholder="Age" @change="handleInput" />

        <input type="checkbox" name="isVerified" id="">
    </div>

    <div>
        <p>{{ displayData }}</p>
    </div>

       
</template>

<style scoped>
.hello {
    color: green
}
</style>