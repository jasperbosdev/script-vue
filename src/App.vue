<script setup>
import { ref } from 'vue'

const tasks = ref([
    { name: 'Boodschappen doen', completed: false },
    { name: 'Afwassen', completed: true },
    { name: 'Hond uitlaten', completed: false },
])

const changeCompleted = (task)=>{
    task.completed = !task.completed
}

</script>

<template>
    <h1 class="font-bold">To-do List</h1>
    <ul>
        <li v-for="(task, index) in tasks" :key="index"
        class="flex gap-2">
            <strong>{{ task.name }}</strong>
            <p @click="changeCompleted(task)" class="cursor-pointer" v-if="task.completed == true">Completed ✅</p>
            <p @click="changeCompleted(task)" class="cursor-pointer" v-else>Not complete ❌</p>
        </li>
    </ul>
</template>