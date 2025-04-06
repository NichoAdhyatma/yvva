<script setup lang="ts">
import { ref, onMounted, nextTick } from 'vue'

const count = ref(0)

const object = ref({
    name: 'John Doe',
    age: 30,
})

const stringHTML = '<h1>Hello World</h1>'

const increment = async () => {
    count.value++

    count.value++

    count.value++

    count.value++

    count.value++

    await nextTick()

    console.log('Count:', count.value)

}

const decrement = () => {
    count.value--
}

const reset = () => {
    count.value = 0
}

onMounted(() => {
    console.info('Onmounted')
})

const classHello = "hello"

const id = "hello"

const disabled = ref(true)

const data = {
    id: "hello",
    class: "hello",
}

const changeName = () => {
    count.value++

    object.value.name = `Jane Doe changed-${count.value}`
}

</script>

<template>
   <p v-bind:class="classHello">Composition API</p>

   <p :id="id">{{ stringHTML }}</p>

   <p>{{ object.name }}</p>

    <p>{{ object.age }}</p>

   <p :class="data.class" v-html="stringHTML" :id="data.id"></p>

    <code v-bind="data">Count is {{ count }}</code>

    <div>
        <button @click="increment">+</button>
        <button @click="decrement">-</button>
        <button :disabled="disabled" @click="reset">Reset</button>
        
        <input placeholder="type here..." type="text" name="text" id="text">
    </div>

    <div>
        <button @click="changeName">change name</button>
    </div>
</template>

<style scoped>

div {
    display: flex;
    gap: 10px;
    justify-content: center;
    margin-top: 10px;
}

.hello {
    color: green;
    font-weight: 600;
}

#hello {
    font-style: italic;
}

</style>