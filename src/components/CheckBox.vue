<script setup>
    const model = defineModel()
    const props=defineProps(['label','value', 'show'])
</script>

<template>
    <div>
   <v-checkbox v-if="show" v-model="model" :value hide-details density="compact" class="shrink mr-0 mt-0" >
     <template v-slot:label ><span v-html="label" class="mylabel" ></span></template>
   </v-checkbox>
</div>
</template>

<style>
.v-label {
    font-size: 0.85em !important;
    opacity: 100% !important;
}
</style>
