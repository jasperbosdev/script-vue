<script setup>
import {ref} from 'vue';
import DiceIcon from './DiceIcon.vue';

const dice = defineModel();
const diceSideCount = ref([0, 0, 0, 0, 0, 0]);
const rolledDice = ref(false);

const diceRoll = () => {
    rolledDice.value = true;
    diceSideCount.value.fill(0);

    for (let i = 0; i < 5; i++) {
        dice.value[i] = Math.floor(Math.random() * 6) + 1;
        diceSideCount.value[dice.value[i] - 1]++;
    }
};

const clearArrs = () => {
    dice.value = [0, 0, 0, 0, 0];
    diceSideCount.value.fill(0);
    rolledDice.value = false;
};
</script>

<template>
    <div class="bg-white/20 rounded-lg p-4">
        <div class="flex gap-2">
            <button @click="diceRoll" class="mb-4 w-full">Roll 5 Dices</button>
            <button v-if="rolledDice" @click="clearArrs" class="mb-4 w-full bg-red-500">Clear</button>
        </div>
        <div class="flex gap-4 p-2 bg-white/20 border border-white/10 rounded-xl">
            <div v-for="(value, index) in diceSideCount" :key="index" class="flex flex-col items-center gap-2">
                <DiceIcon :value="index + 1" />
                <p class="font-semibold p-2 bg-zinc-800/80 rounded w-10">{{ value }}</p>
            </div>
        </div>
    </div>
</template>
