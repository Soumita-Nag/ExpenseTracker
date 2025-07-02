<template>
  <div class="text-center p-4 bg-gray-800 rounded-md shadow-md mb-5">
    <h3 class="text-gray-400 text-sm uppercase font-medium">
      Your Balance
    </h3>
    <h2 class="text-3xl font-bold text-white mt-1" :class="balance<0?'minus':'plus'">
      ₹{{ balance }}
    </h2>
  </div>
</template>

<script setup>
    import { defineProps } from "vue";
    const props=defineProps({
        balance:{
            type:Number,
            required:true
        }
    })
</script>

<style scoped>
.plus{
  color: #22c55e;
}
.minus{
  color: #fb2c36;
}
</style>
