<script setup>
    const props=defineProps({
        url: String
    })
    const hasImage = props.url ? true : false
</script>

<template>
    <v-menu open-on-click>
        <template v-slot:activator="{ props }">
            <v-avatar v-if="hasImage" :image="url" v-bind="props"></v-avatar>
            <v-avatar v-else :props icon="mdi-account-circle" color="primary"  v-bind="props"></v-avatar>
        </template>
        <v-list>
            <v-list-item prepend-icon="mdi-account-circle" title="Profile" value=""></v-list-item>
            <v-divider></v-divider>
            <v-list-item prepend-icon="mdi-logout" title="Logout" value=""></v-list-item>
        </v-list>
    </v-menu>
</template>