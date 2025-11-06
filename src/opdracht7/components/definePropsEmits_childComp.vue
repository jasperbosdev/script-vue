<script setup>
defineProps({
    message: String,
});

const emit = defineEmits(['updateMessage']);

const updateMessage = () => {
    emit('updateMessage', 'Nieuw bericht van Child Component');
};
</script>

<template>
    <p>child file:</p>
    <br />
    {{ message }}
    <br/>
    <button @click="updateMessage">Send Message</button>
</template>
