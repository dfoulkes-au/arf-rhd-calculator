<script setup>
  import CheckBox from './CheckBox.vue'

  const model = defineModel()
  const props=defineProps(['cinfo'])
</script>

<template>
  <v-card class ="mx-auto" width="600">
    <div class="bg-teal">
    <v-card-title>
      <h2 class="font-weight-light">
        <v-icon icon="mdi-heart-pulse" class="me-4" start />
        {{ cinfo.title }}
      </h2>
    </v-card-title >
    <v-card-subtitle >
        {{ cinfo.subtitle }}
    </v-card-subtitle>
    </div>  
    <v-card-text class="leadout">
        <CheckBox v-for="item in cinfo.items" v-model="model" :label="item.label" :value="item.value" :show="item.show" />
        <div v-if="cinfo.statement" class="statement my-3">{{ cinfo.statement }}</div>
        <div v-for="note in cinfo.leadout" class="leadout mt-2">{{ note }}</div>
        <v-divider v-if="(cinfo.leadout.length > 0) && (cinfo.disclaimer.length > 0)"></v-divider>
        <div v-if="cinfo.disclaimer.length > 0" class="mt-3">
          <div v-for="note in cinfo.disclaimer" class="disclaimer my-0">{{ note }}</div>
        </div>
        
        
    </v-card-text>
    <v-card-actions>
        <v-btn v-if="cinfo.prev != ''" class="text-teal":text="cinfo.prev" @click="$emit('toPage', -1)" />
        <v-btn v-if="cinfo.next != ''" class="ms-auto text-teal" :text="cinfo.next" @click="$emit('toPage', 1)" />
    </v-card-actions>
  </v-card>
</template>

<style>
.leadout {
  font-size: 1em;
  opacity: 100;
}
.statement {
  font-size: 1.5em;
  font-weight: 500;
}
.disclaimer {
  font-size: 1em;
  font-weight: 500;
  color: red;
}
</style>