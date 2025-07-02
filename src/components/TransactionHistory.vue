<template>
  <div class="p-4 bg-gray-800 rounded-md shadow-md mt-5">
    <h3 class="text-2xl font-semibold text-white mb-4 border-b border-gray-600 pb-2">
      Transaction History
    </h3>

    <div v-for="item in transactions" :key="item.id" :class="item.cost>=0?'plus':'minus'" class="flex justify-between items-center bg-gray-700 text-gray-100 px-4 py-2 rounded mb-2 shadow-sm">
      <h4 class="font-medium">{{ item.text }}</h4>
      <h4 class="font-semibold">₹{{ (item.cost )<0?item.cost*(-1):item.cost}}</h4>
      <!-- <button class="">X</button> -->
    </div>
  </div>
</template>

<script setup>
    import {defineProps} from 'vue';
    const props= defineProps({
        transactions:{
            type: Array,
            required: true,
        }
    })
</script>

<style scoped>
    .plus{
        /* color: green; */
        border-right: 5px solid green;
    }
    .minus{
        /* color: red; */
        border-right: 5px solid red;
    }
</style>
