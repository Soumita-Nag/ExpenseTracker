<template>
  <div class="text-center p-4 bg-gradient-to-br from-purple-900 via-violet-800 to-pink-700 rounded-md shadow-md mb-5 border border-pink-400/30">
    <h3 class="text-pink-200 text-sm uppercase font-medium">
      Total Balance
    </h3>
    <h2 class="text-3xl font-bold mt-1">
      ₹{{ balance }}
    </h2>
  </div>
</template>

<script setup>
import { defineProps } from "vue";
const props = defineProps({
  balance: {
    type: Number,
    required: true
  }
});
</script>

<style scoped>
</style>
