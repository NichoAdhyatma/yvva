        
<script setup lang="ts">

  
    const [name, nameModifiers] = defineModel<string>("name", {
        required: true,
        type: String,
        default: () => 'nico@gmail.com',
        get(value) {
            if(nameModifiers.uppercase) {
                return value.toUpperCase()
            }
            return value
        }
    })

    const age = defineModel<number>("age", {
        required: true,
        type: Number,
        default: () => 20
    })

    const emit = defineEmits<{
        clearForm: [],
    }>()

    const clearForm = () => {
        emit('clearForm')
    }
</script>
<template>
    <div>
        <h1>Contact Preview</h1>

        <div>
            <pre>{{ name }}</pre>
  
            <pre>{{ age }}</pre>
        </div>

        <button @click="clearForm">Clear Form</button>
    </div>
</template>

<style scoped>

</style>