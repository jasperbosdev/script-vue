<script setup>
defineProps({
    value: {
        type: Number,
        required: true,
        validator: val => val >= 1 && val <= 6,
    },
});
</script>

<template>
    <!-- Dice 1 -->
    <svg
        v-if="value === 1"
        width="48"
        height="48"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
        class="icon icon-tabler icons-tabler-outline icon-tabler-dice-1"
    >
        <path stroke="none" d="M0 0h24v24H0z" fill="none" />
        <path d="M3 3m0 2a2 2 0 0 1 2 -2h14a2 2 0 0 1 2 2v14a2 2 0 0 1 -2 2h-14a2 2 0 0 1 -2 -2z" />
        <circle cx="12" cy="12" r=".5" fill="currentColor" />
    </svg>

    <!-- Dice 2 -->
    <svg
        v-else-if="value === 2"
        width="48"
        height="48"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
        class="icon icon-tabler icons-tabler-outline icon-tabler-dice-2"
    >
        <path stroke="none" d="M0 0h24v24H0z" fill="none" />
        <path d="M3 3m0 2a2 2 0 0 1 2 -2h14a2 2 0 0 1 2 2v14a2 2 0 0 1 -2 2h-14a2 2 0 0 1 -2 -2z" />
        <circle cx="9.5" cy="9.5" r=".5" fill="currentColor" />
        <circle cx="14.5" cy="14.5" r=".5" fill="currentColor" />
    </svg>

    <!-- Dice 3 -->
    <svg
        v-else-if="value === 3"
        width="48"
        height="48"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
        class="icon icon-tabler icons-tabler-outline icon-tabler-dice-3"
    >
        <path stroke="none" d="M0 0h24v24H0z" fill="none" />
        <path d="M3 3m0 2a2 2 0 0 1 2 -2h14a2 2 0 0 1 2 2v14a2 2 0 0 1 -2 2h-14a2 2 0 0 1 -2 -2z" />
        <circle cx="9.5" cy="9.5" r=".5" fill="currentColor" />
        <circle cx="12" cy="12" r=".5" fill="currentColor" />
        <circle cx="14.5" cy="14.5" r=".5" fill="currentColor" />
    </svg>

    <!-- Dice 4 -->
    <svg
        v-else-if="value === 4"
        width="48"
        height="48"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
        class="icon icon-tabler icons-tabler-outline icon-tabler-dice-4"
    >
        <path stroke="none" d="M0 0h24v24H0z" fill="none" />
        <path d="M3 3m0 2a2 2 0 0 1 2 -2h14a2 2 0 0 1 2 2v14a2 2 0 0 1 -2 2h-14a2 2 0 0 1 -2 -2z" />
        <circle cx="9.5" cy="9.5" r=".5" fill="currentColor" />
        <circle cx="14.5" cy="9.5" r=".5" fill="currentColor" />
        <circle cx="9.5" cy="14.5" r=".5" fill="currentColor" />
        <circle cx="14.5" cy="14.5" r=".5" fill="currentColor" />
    </svg>

    <!-- Dice 5 -->
    <svg
        v-else-if="value === 5"
        width="48"
        height="48"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
        class="icon icon-tabler icons-tabler-outline icon-tabler-dice-5"
    >
        <path stroke="none" d="M0 0h24v24H0z" fill="none" />
        <path d="M3 3m0 2a2 2 0 0 1 2 -2h14a2 2 0 0 1 2 2v14a2 2 0 0 1 -2 2h-14a2 2 0 0 1 -2 -2z" />
        <circle cx="9.5" cy="9.5" r=".5" fill="currentColor" />
        <circle cx="14.5" cy="9.5" r=".5" fill="currentColor" />
        <circle cx="9.5" cy="14.5" r=".5" fill="currentColor" />
        <circle cx="14.5" cy="14.5" r=".5" fill="currentColor" />
        <circle cx="12" cy="12" r=".5" fill="currentColor" />
    </svg>

    <!-- Dice 6 -->
    <svg
        v-else-if="value === 6"
        width="48"
        height="48"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
        class="icon icon-tabler icons-tabler-outline icon-tabler-dice-6"
    >
        <path stroke="none" d="M0 0h24v24H0z" fill="none" />
        <path d="M3 3m0 2a2 2 0 0 1 2 -2h14a2 2 0 0 1 2 2v14a2 2 0 0 1 -2 2h-14a2 2 0 0 1 -2 -2z" />
        <circle cx="9.5" cy="8" r=".5" fill="currentColor" />
        <circle cx="9.5" cy="12" r=".5" fill="currentColor" />
        <circle cx="9.5" cy="16" r=".5" fill="currentColor" />
        <circle cx="14.5" cy="8" r=".5" fill="currentColor" />
        <circle cx="14.5" cy="12" r=".5" fill="currentColor" />
        <circle cx="14.5" cy="16" r=".5" fill="currentColor" />
    </svg>
</template>
