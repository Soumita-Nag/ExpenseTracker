<template>
  <div class="flex justify-center w-full px-4">
    <div class="w-full flex gap-4">
      <!-- Income Box -->
      <div class="flex flex-col justify-center items-center w-1/2 p-6 rounded-xl bg-gray-800 text-white shadow-md">
        <h3 class="text-lg font-semibold uppercase">Income</h3>
        <h3 class="text-2xl font-bold mt-2 text-green-500">₹{{ income }}</h3>
      </div>

      <!-- Expense Box -->
      <div class="flex flex-col justify-center items-center w-1/2 p-6 rounded-xl bg-gray-800 text-white shadow-md">
        <h3 class="text-lg font-semibold uppercase">Expense</h3>
        <h3 class="text-2xl font-bold mt-2 text-red-500">₹{{ expenses*(-1) }}</h3>
      </div>
    </div>
  </div>
</template>

<script setup>
  import { defineProps } from "vue";
  const props=defineProps({
    income:{
      type:Number,
      required:true
    },
    expenses:{
      type:Number,
      required:true
    }
  })
</script>

<style scoped>
</style>
