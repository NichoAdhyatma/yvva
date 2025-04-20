
<script setup lang="ts">

import ContactForm from './ContectForm.vue';
import ContactPreview from './ContactPreview.vue';

import Card from './Card.vue';

import Button from './Button.vue';
export type Contact = {
    name: string,
    email: string,
    age: number,
    type: string,
    complain: boolean,
    message: string
}

import { reactive } from 'vue';


const contact = reactive<Contact>({
    name: '',
    email: '',
    age: 0,
    type: 'Regular',
    complain: false,
    message: ''
})

const clearForm = () => {
    contact.name = ''
    contact.email = ''
    contact.age = 0
}

const handleClick = (value: string) => {
    alert('Button clicked from emit ' + value)
}

const handleClick2 = () => {
    alert('Button clicked from props')
}

</script>


<template>
    <div>
    
<!--         
        <ContactForm v-model="contact" />

       <ContactPreview v-model:name.uppercase="contact.name" v-model:age="contact.age" @clear-form="clearForm" />

       <Button label="Clear" class="button" :onClick="handleClick2" @emit-click="handleClick" /> -->

       <Card title="Contact Us">
        <template #header="props">
            <p>Header {{ props.counter }}</p>
        </template>
        <template #content="props">
            <p>Click  Me</p>
            <Button label="Clear" class="button" :onClick="handleClick2" @emit-click="handleClick" />
        </template>
        <template #footer>
            <p>Copyright @ {{ new Date().getFullYear() }}</p>
        </template>
       </Card>

       <Card title="Blank Card">
       
       </Card>

    </div>
</template>



<style scoped>
div {
    flex-direction: column;
}

form {
    display: flex;
    flex-direction: column;
    gap: 10px;
}

pre {
    background-color: #f0f0f0;
    padding: 10px;
    border-radius: 5px;
    font-size: 12px;
    font-family: monospace;
    white-space: pre-wrap;
    word-wrap: break-word;
    overflow-wrap: break-word;
}

.button {
    background-color: #000;
    color: #fff;
    padding: 10px;
    border-radius: 5px;
    cursor: pointer;
}

</style>