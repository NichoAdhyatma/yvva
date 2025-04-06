
<script setup lang="ts">
import { ref } from 'vue';

const score = ref<number>(0)

const changeScore = (value: number) => {
    score.value = value
}

const classScore = ref({
    cool: false,
    good: false,
    bad: false
})

const changeClass = (value: number) => {
    classScore.value = {
        cool: value === 100,
        good: value === 50,
        bad: value === 0
    }
}

</script>

<template>
    <div>
        <p v-if="score != undefined" :class="classScore">your score is {{ score }}</p>
    </div>

    <p v-if="score <= 100 && score >= 50">✅</p>
    <p v-if="score === 0">❌</p>

    <div>
        <button @click="() => {changeScore(100) 
            changeClass(100)}">cool score</button>
        <button @click="() => {changeScore(50)
            changeClass(50)
        }">good score</button>
        <button @click="() => {changeScore(0) ;
            changeClass(0)}">bad score</button>
    </div>
</template>



<style scoped>
.cool {
    color: blue;
}

.good {
    color: green;
}

.bad {
    color: red;
}

</style>