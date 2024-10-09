<template>
  <button class="border border-gray-300 bg-white w-full h-20 text-xl text-gray-800 cursor-pointer">
    {{ button }}
  </button>
</template>

<script setup lang="ts">
import { defineProps } from 'vue'

defineProps({
  button: {
    type: String,
    required: true,
    default: ''
  }
});
</script>
