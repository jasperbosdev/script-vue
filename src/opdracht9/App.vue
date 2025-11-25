<script setup>
import {ref} from 'vue';
import ScoreTable from './components/ScoreTable.vue';
import ThrownDice from './components/ThrownDice.vue';

const dice = ref([0, 0, 0, 0, 0]);
</script>

<template>
    <p class="py-4 text-2xl font-semibold">Yahtzee</p>
    <div class="flex flex-col gap-4 w-full">
        <div>
            <ThrownDice v-model="dice" />
        </div>
        <div>
            <ScoreTable v-model="dice" />
        </div>
    </div>
</template>
