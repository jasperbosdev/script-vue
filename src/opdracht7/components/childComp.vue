<template>
    <p class="mb-1">child file content:</p>
    <div class="flex flex-col p-4 bg-white/20 rounded-lg border border-white/10">
        <div class="flex flex-col">
            <label class="font-semibold mb-1">Message:</label>
            <input v-model="message" placeholder="message" class="p-1 rounded-lg" />
        </div>
    </div>
</template>

<script setup>
const message = defineModel();
</script>
