<script setup lang="ts">
import { ref } from 'vue';

const todos = ref([
    {
        id: 1,
        title: 'Todo 1',
        completed: true
    },
    {
        id: 2,
        title: 'Todo 2',
        completed: true
    },
    {
        id: 3,
        title: 'Todo 3',
        completed: false
    }
])

const handleCheckTodo = (event: Event) => {
    const input = event.target as HTMLInputElement

    const todoId = parseInt(input.id)

    const todo = todos.value.find(todo => todo.id === todoId)

    if (todo) {
        todo.completed = input.checked
    }
}


</script>

<template>
    <div>
        <h1>Todo List</h1>
        <ul>
            <li v-for="todo in todos" :key="todo.id">
                <input type="checkbox" @input="handleCheckTodo" :checked="todo.completed"  :id="todo.id.toString()"/>
                {{ todo.title }}

                <p>{{ todo.completed ? 'completed' : 'none' }}</p>
            </li>
        </ul>

        <ul v-for="todo in todos" :key="todo.id">
            <li v-for="(value, key) in todo" :key="key">
                {{ key }}: {{ value }}
            </li>
        </ul>

        <div v-for="n in 10" :key="n">
            <p>{{ n }}</p>
            <p v-if="n % 2 === 0">even</p>
            <p v-else>odd</p>

        </div>

        <button @click="() => {
            console.log('Hello')
         
            console.log('Hello 2')
        }">Hello</button>
    </div>
</template>



<style scoped>

div {
    flex-direction: column;
}

</style>