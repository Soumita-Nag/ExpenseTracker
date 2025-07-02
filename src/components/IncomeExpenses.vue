<template>
  <div class="flex justify-center w-full">
    <div class="w-full flex gap-4">
      <!-- Income Box: purple-pink blend, leaning purple -->
      <div class="flex flex-col justify-center items-center w-1/2 p-6 rounded-xl bg-gradient-to-br from-purple-900 via-purple-700 to-pink-600 text-white shadow-md">
        <h3 class="text-lg font-semibold uppercase text-purple-200">Income</h3>
        <h3 class="text-2xl font-bold mt-2 text-white">₹{{ income }}</h3>
      </div>

      <!-- Expense Box: pink-purple blend, leaning pink -->
      <div class="flex flex-col justify-center items-center w-1/2 p-6 rounded-xl bg-gradient-to-tl from-pink-700 via-pink-600 to-purple-700 text-white shadow-md">
        <h3 class="text-lg font-semibold uppercase text-pink-200">Expense</h3>
        <h3 class="text-2xl font-bold mt-2 text-white">₹{{ expenses * -1 }}</h3>
      </div>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from "vue";    
const props = defineProps({
  income: {
    type: Number,
    required: true
  },
  expenses: {
    type: Number,
    required: true
  }
});
</script>

<style scoped>
</style>
