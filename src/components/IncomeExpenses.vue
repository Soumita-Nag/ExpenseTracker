<template>
  <div class="flex justify-center w-full">
    <div class="w-full flex flex-col sm:flex-row gap-4">

      <!-- Balance Box -->
      <div class="flex flex-col justify-center items-center h-full w-full sm:w-1/3 p-1 rounded-xl text-white bg-gradient-to-br from-purple-700 to-pink-700 ">
        <div class="bg-purple-950/80 flex flex-col justify-center items-center w-full p-6 rounded-xl ">
          <h3 class="text-lg font-semibold uppercase text-purple-200">Total Balance</h3>
          <h3 class="text-2xl font-bold mt-2 text-white">₹{{ balance.toFixed(2) }}</h3>
        </div>
      </div>

      <!-- Income Box -->
      <div class="flex flex-col justify-center items-center h-full w-full sm:w-1/3 p-1 rounded-xl text-white bg-gradient-to-br from-purple-700 to-pink-700 ">
        <div class="bg-purple-950/80 flex flex-col justify-center items-center w-full p-6 rounded-xl ">
          <h3 class="text-lg font-semibold uppercase text-purple-200">Income</h3>
          <h3 class="text-2xl font-bold mt-2 text-white">₹{{ income.toFixed(2) }}</h3>
        </div>
      </div>

      <!-- Expense Box -->
      <div class="flex flex-col justify-center items-center w-full sm:w-1/3 p-1 rounded-xl text-white bg-gradient-to-br from-purple-700 to-pink-700 ">
        <div class="bg-purple-950/80 flex flex-col justify-center items-center w-full p-6 rounded-xl ">
          <h3 class="text-lg font-semibold uppercase text-purple-200">Expense</h3>
          <h3 class="text-2xl font-bold mt-2 text-white">₹{{ (expenses*(-1)).toFixed(2) }}</h3>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from "vue";    
const props = defineProps({
  balance: {
    type: Number,
    required: true
  },
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
