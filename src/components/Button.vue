<script setup lang="ts">
import { useAttrs } from 'vue';

type ButtonProps = {
    label: string
    onClick: () => void
}

    const props = defineProps<ButtonProps>()

    type EmitsButton = {
        emitClick: [string]
    }

    const emits = defineEmits<EmitsButton>()

    const handleClick = () => {
        props.onClick()
        emits('emitClick', 'nico')
    }

    const attributes = useAttrs()

    console.log(attributes)

</script>
<template>
   <button @click="handleClick" v-bind="attributes">{{ props.label }}</button>
</template>


<style scoped>

</style>