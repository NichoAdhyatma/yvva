<script setup lang="ts">
    import type { PropType } from 'vue';
import type { Contact } from './ContactUs.vue';

    const model = defineModel<Contact>({
        required: true,
        type: Object as PropType<Contact>,
        default: () => ({
            name: 'Nico'
        })
    })

    const handleSubmit = () => {
        console.log(model.value)
    }
</script>

<template>
    <div>
        <form @submit.prevent="handleSubmit">
            <input type="text" v-model.lazy="model.name" placeholder="Name">
            <input type="email" v-model.lazy="model.email" placeholder="Email">
            <input type="text" v-model.number="model.age" placeholder="Age">
           
            <select v-model="model.type">
                <option value="Regular">Regular</option>
                <option value="VIP">VIP</option>
                <option value="Complaint">Complaint</option>
            </select>

            <div>
                <label for="complain">Complain</label>
                <input id="complain" type="checkbox" v-model="model.complain" placeholder="Complain">
                {{ model.complain }}
            </div>

            <textarea v-model="model.message" placeholder="Message"></textarea>

            <button type="submit">Submit</button>
        </form>
    </div>
</template>

<style scoped>

form {
    display: flex;
    flex-direction: column;
    gap: 20px;
}

select, textarea {
    padding: 6px;
    border-radius: 8px;
    border: 1px solid #000000;
}


</style>