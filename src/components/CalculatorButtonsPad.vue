<template>
  <div class="grid grid-cols-4 gap-2">
    <CalculatorButton
      v-for="button in buttons"
      :key="button"
      :button="button"
      @click="$emit('button-click', button)"
    />
  </div>
</template>

<script setup lang="ts">
import { defineProps, defineEmits } from 'vue'
import type { EmitFn } from 'vue'
import CalculatorButton from '@/components/CalculatorButton.vue'

defineProps({
  buttons: {
    type: Array,
    required: true,
    default: () => ([])
  }
});

const $emit:EmitFn<"button-click"[]> = defineEmits(['button-click']);
</script>
