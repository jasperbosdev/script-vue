<!-- Wist niet zo goed waar ik 2 buttons voor moest gebruiken, dus ik heb maar een knop voor een voorbeeld firstName en country gemaakt. -->

<script setup>
import {ref, reactive} from 'vue';

const clicks = ref(0);
const person = reactive({
    firstName: '',
    country: '',
});
</script>

<template>
    <p>Clicks count: {{ clicks }}</p>
    <button @click="clicks++">Increment clicks</button>

    <div class="mt-4">
        <p>Naam en Land</p>
        <form class="flex flex-col gap-2" @submit.prevent="onSubmit">
            <div class="flex gap-4">
                <input v-model="person.firstName" placeholder="Wat is uw voornaam?" />
                <button @click="person.firstName = 'Jan'">
                    Jan
                </button>
            </div>
            <p>{{ person.firstName }}</p>
            <div class="flex gap-4">
                <input v-model="person.country" placeholder="Waar bevind u zich?" />
                <button @click="person.country = 'Nederland'">
                    NL
                </button>
            </div>
            <p>{{ person.country }}</p>
            <!-- <button>Submit</button> -->
        </form>
    </div>
</template>
