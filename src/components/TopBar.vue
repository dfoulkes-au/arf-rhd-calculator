<script setup>
    import ProfilePic from "./ProfilePic.vue"
    import ButtonTip from "./ButtonTip.vue"
</script>

<template>
<v-app-bar>
    <template v-slot:prepend>
        <v-app-bar-nav-icon></v-app-bar-nav-icon>
    </template>
    <v-btn icon="mdi-heart-pulse" color="teal"></v-btn>
    <v-app-bar-title>Acute Rheumatic Fever - Jones Criteria Calculator</v-app-bar-title>
    <template v-slot:append>
        <ButtonTip icon="mdi-account-multiple" tip="Show patient list"></ButtonTip>        
        <v-sheet class="mx-auto" width="300">
            <v-text-field
                append-inner-icon="mdi-magnify"
                density="compact"
                label="Search for patient"
                variant="solo"
                hide-details
                single-line
                >
            </v-text-field>
        </v-sheet>
        <v-btn icon="mdi-dots-vertical"></v-btn>
        <ProfilePic url="https://randomuser.me/api/portraits/men/85.jpg"></ProfilePic>
    </template>
</v-app-bar>
</template>