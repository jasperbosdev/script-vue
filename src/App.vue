<script setup lang="ts">
import {computed, ref} from 'vue';

let people = ref([
    {name: 'Jan', age: 18},
    {name: 'Piet', age: 20},
]);

const adults = computed(() => {
    return people.value.filter(person => person.age >= 18);
});

const children = computed(() => {
    return people.value.filter(person => person.age < 18);
});

const name = ref('');
const age = ref();

const formSubmit = () => {
    if (name.value != '' && age.value != '') {
        people.value.push({name: name.value, age: age.value});
    }
};
</script>

<template>
    <div>
        <h1>Computed met .filter()</h1>
        <div class="mt-4 gap-4 flex flex-col max-w-[300px] mx-auto border border-white/5 rounded-lg bg-white/10 p-4">
            <div class="flex flex-col">
                <label class="font-semibold">Naam:</label>
                <input type="text" placeholder="naam" class="rounded-lg py-1 px-2 mt-1 bg-white/10" v-model="name" />
            </div>
            <div class="flex flex-col">
                <label class="font-semibold">Leeftijd:</label>
                <input
                    type="number"
                    placeholder="leeftijd"
                    min="1"
                    max="99"
                    class="rounded-lg py-1 px-2 mt-1 bg-white/10"
                    v-model="age"
                />
            </div>
            <button @click="formSubmit">Submit</button>
        </div>
        <div class="flex flex-col gap-2 mt-4 max-w-[500px] mx-auto border border-white/5 rounded lg bg-white/10 p-4">
            <h3 class="w-full font-semibold">Array values:</h3>
            <div class="flex gap-4">
                <div class="w-full">
                    <p class="font-semibold mb-2">Adults</p>
                    <div class="rounded-lg p-2 bg-white/10">
                        <li v-for="person in adults" :key="person.id" class="list-none">
                            {{ person.name }}: {{ person.age }}
                        </li>
                    </div>
                </div>
                <div class="w-full">
                    <p class="font-semibold mb-2">Children</p>
                    <div class="rounded-lg p-2 bg-white/10">
                        <li v-for="person in children" :key="person.id" class="list-none">
                            {{ person.name }}: {{ person.age }}
                        </li>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
