<script setup>
    const model = defineModel()
    const props=defineProps(['label','value', 'show'])
</script>

<template>
   <v-checkbox v-if="show" v-model="model" :value hide-details density="compact" class="shrink mr-0 mt-0 label" >
    <template v-slot:label><span v-html="label" class="label"></span></template>
   </v-checkbox>
</template>

<style>
.v-label {
    opacity: 100%;
    font-size: 0.85em;
}
</style>
