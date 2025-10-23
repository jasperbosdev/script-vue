<script setup>
import {ref, computed} from 'vue';
import './style.css';

const header = ref('Shopping List App');
const characterCount = computed(() => {
    return newItem.value.length;
});
const editing = ref(false);
const items = ref([
    {id: 1, label: '10 party hats', purchased: true, highPriority: false},
    {id: 2, label: '2 board games', purchased: true, highPriority: false},
    {id: 3, label: '20 cups', purchased: false, highPriority: true},
]);
const reversedItems = computed(()=>[...items.value].reverse())
const newItem = ref('');
const newItemHighPriority = ref(false);
const saveItem = () => {
    items.value.push({id: items.value.length + 1, label: newItem.value, highPriority: newItemHighPriority.value});
    newItem.value = '';
    newItemHighPriority.value = '';
};
const doEdit = e => {
    editing.value = e;
    newItem.value = '';
    newItemHighPriority.value = '';
};
const togglePurchased = item => {
    item.purchased = !item.purchased;
};
</script>

<template>
    <header class="mb-5 flex flex-col gap-5 items-center">
        <h1 class="text-white font-bold">{{ header }}</h1>
        <button class="btn w-fit" @click="doEdit(false)" v-if="editing">Cancel</button>
        <button v-else @click="doEdit(true)" class="btn btn-primary w-fit">Add Item</button>
    </header>
    <form
        class="border rounded-lg flex flex-col justify-center items-center p-4 gap-4"
        @submit.prevent="saveItem"
        v-if="editing"
    >
        <input
            type="text"
            v-model.trim="newItem"
            placeholder="Add an item"
            class="w-full px-2 py-1 border rounded-lg"
        />
        <p class="text-xs">{{ characterCount }}/200</p>
        <label>
            <input type="checkbox" v-model="newItemHighPriority" />
            High Priority
        </label>
        <button :disabled="newItem.length < 5" class="disabled:bg-gray-700 w-fit btn btn-primary">Save Item</button>
    </form>
    <br />
    <ul>
        <li
            class="cursor-pointer"
            @click="togglePurchased(item)"
            v-for="(item) in reversedItems"
            :key="item.id"
            :class="{strikeout: item.purchased, priority: item.highPriority}"
        >
            {{ item.label }}
        </li>
    </ul>
    <p v-if="!items.length">No items in the list</p>
</template>
