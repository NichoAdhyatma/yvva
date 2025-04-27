<script setup lang="ts">
import { inject } from 'vue';
import type { ProfileType } from './type';
import CounterStateless from '../CounterStateless.vue';


const profile = inject<ProfileType>('profile')

const props = defineProps<{
    stringArgs: string
}>()

const onClick = () => {
    if(profile === undefined) {
        return
    }
    profile.email = "nicho@gmail.com"
}


</script>

<template>
    <div>
        <h1>Profile Data</h1>
        <p>{{ profile?.name }}</p>

        <p>{{ profile?.email }}</p>

        <button @click="onClick"> change email</button>

  

        <CounterStateless name="Nico" :counter="0" @increment="onClick"/>
    </div>

</template>


<style scoped>

</style>