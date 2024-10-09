<template>
  <div class="w-96 mx-auto text-center">
    <CalculatorDisplay v-model="display" :lastOperation="lastOperation" />
    <CalculatorButtonsPad :buttons="buttons" @button-click="handleButtonClick" />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { evaluate } from 'mathjs'
import buttonsConfig from './helpers/buttonsConfig'
import CalculatorDisplay from '@/components/CalculatorDisplay.vue'
import CalculatorButtonsPad from '@/components/CalculatorButtonsPad.vue'

const display = ref('');
const lastOperation = ref('');
const buttons = buttonsConfig;

const handleButtonClick = (button) => {
  if (button === 'AC') {
    display.value = ''
    lastOperation.value = ''

    return
  }

  if (button === '=') {
    if (display.value.trim() === '') {
      display.value = 'Error';
      return;
    }

    try {
      lastOperation.value = display.value;
      display.value = evaluate(display.value).toString();
    } catch (error) {
      display.value = 'Error';
    }
  } else {
    display.value += button;
  }
};
</script>

<style scoped>
</style>
