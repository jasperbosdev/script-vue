<script setup>
    import childComp from './components/childComp.vue';
    import { ref } from 'vue';

    const message = ref('')
</script>

<template>
    <p>parent file:</p><br/>
    <p>{{ message }}</p>
    <childComp v-model="message"/>
</template>