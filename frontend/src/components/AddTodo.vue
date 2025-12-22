<script setup lang="ts">
import { ref } from 'vue'

const todos = defineModel("todos")

const newTitle = ref('')
const nextId = ref(Math.max(0, ...todos.value.map(todo => todo.id)) + 1)

function addTodo() {
  const title = newTitle.value;
  todos.value.push({ id: nextId.value++, title, completed: false });
  newTitle.value = '';
}
</script>


<template>
    <section>
        <h2>New Todo</h2>
        <div style="display: flex; align-items: center; gap: 0.5em; margin: 0.25em 0;">
            <input type="text" v-model="newTitle" placeholder="New Todo title" aria-label="New Todo title" />
        <button v-on:click="addTodo" :disabled="!newTitle">Add</button>
        </div>
    </section>
</template>