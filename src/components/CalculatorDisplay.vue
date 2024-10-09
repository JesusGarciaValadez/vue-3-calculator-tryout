<template>
  <div class="mb-4 border border-2 bg-amber-100 py-1 px-4">
    <div v-if="lastOperation" class="text-xs text-gray-800 text-right mb-1">
      {{ lastOperation }}
    </div>
    <input
      type="text"
      v-model="display"
      readonly
      aria-readonly="true"
      class="w-full h-10 text-2xl text-gray-800 text-right bg-transparent"
    />
  </div>
</template>

<script setup>
import { defineProps } from 'vue';

const display = defineModel({
  type: String,
  required: true
})

defineProps({
  lastOperation: {
    type: String,
    required: false
  }
});
</script>
