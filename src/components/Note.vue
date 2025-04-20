 <script setup lang="ts">
import { reactive, ref, useTemplateRef, nextTick } from 'vue';

 type Note = {
    id: number
    title: string
    content: string
}

 const notes = reactive<Note[]>([])

 const note = ref<Note>({
    id: 0,
    title: "",
    content: ""
 })


 const titleInput = useTemplateRef("titleInput")

 const contentInput = useTemplateRef("contentInput")

 const notesRef = useTemplateRef("noteList")


 const addNote = async () => {
    notes.push({
        id: notes.length + 1,
        title: note.value.title,
        content: note.value.content
    })

    note.value.title = ""

    note.value.content = ""
    
    titleInput.value?.focus()

    await nextTick()

    if(notesRef.value) {
        notesRef.value.forEach(note => {
            console.info(note.textContent)
        })
    }
 }
</script>

<template>
    <div>
        <input type="text" v-model="note.title" placeholder="Title" ref="titleInput" @keydown.enter="contentInput?.focus()" />

        <input type="text" v-model="note.content" placeholder="Content" ref="contentInput" @keydown.enter="addNote" />

        <button @click="addNote">Add Note</button>

        <div v-for="note in notes" :key="note.id" ref="noteList">
            <h3>{{ note.title }}</h3>
            <p>{{ note.content }}</p>
        </div>
    </div>
</template>


<style scoped>
div {
    display: flex;
    flex-direction: column;
    gap: 10px;
}

</style>