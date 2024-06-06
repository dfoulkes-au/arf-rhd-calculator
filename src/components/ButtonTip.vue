<script setup>
    const props=defineProps({
        tip: String,
        icon: String,
        text: String
    })
</script>

<template>
    <v-tooltip :text="tip">
        <template v-slot:activator="{ props }">
            <v-btn v-bind="props" :icon="icon"></v-btn>
        </template>
    </v-tooltip>
</template>