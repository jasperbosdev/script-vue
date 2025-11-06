<script setup>

import { ref } from 'vue';

let rolledInt = ref(0)

let previousRolls = ref([])

const rollDice = () => {
    previousRolls.value.push(rolledInt.value = Math.floor(Math.random() * 6) + 1)
}

const clear = () => {
    previousRolls.value.splice(0)
    rolledInt = 0
}


</script>

<template>
    <p class="text-4xl">Opdracht 8, Vue Dobbelstenen</p>
    <div class="flex flex-col gap-4 rounded-lg bg-white/20 border border-white/10 max-w-[300px] mx-auto mt-4 p-4">
        <p class="font-semibold w-full">opdracht content</p>
        <div class="flex flex-col">
            <button class="select-none" @click="rollDice">Roll dice</button>
            <p v-if="rolledInt != 0" class="mt-2 font-semibold bg-zinc-800/80 p-1 rounded-lg">
                you rolled: {{ rolledInt }}
            </p>
        </div>
        <div v-if="previousRolls != ''" class="flex flex-col bg-zinc-800/80 rounded-lg max-h-[200px] overflow-y-auto">
            <p class="my-1 font-semibold">previous rolls:</p>
            <li v-for="(value) in previousRolls" class="list-none p-1">
                {{ value }}
            </li>
        </div>
        <button v-if="previousRolls != ''" @click="clear">Clear</button>
    </div>
</template>