<script setup lang="ts">
import { provide, reactive } from 'vue';
import type { ProfileType } from './type';
import Profile from './Profile.vue';

        
const profile = reactive<ProfileType>({
    name: 'John Doe',
    
    email: 'nicholaus783@gmail.com'
    })

provide('profile', profile)

const onClick = () => {
    profile.email = "nicho@gmail.com"
}
</script>

<template>
    <div>
        <h1>Profile App Data</h1>
        <p>{{ profile.name }}</p>

        <p>{{ profile.email }}</p>

        <button @click="onClick">Chang email</button>

        <Profile string-args="aa"/>

    </div>
</template>


<style scoped>
div {
    flex-direction: column;
}
</style>