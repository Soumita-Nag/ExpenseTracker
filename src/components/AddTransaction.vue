<template>
  <div class="mx-auto mt-5 p-6 bg-gradient-to-br from-purple-900 via-violet-800 to-pink-700 shadow-md rounded-xl transition-all duration-300 border border-pink-400/30">
    <div class="mb-6">
      <h3 class="text-2xl font-semibold text-white pb-2 border-b border-pink-300">
        Add New Transaction
      </h3>
    </div>

    <form @submit.prevent class="space-y-6 w-full">
      <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
        <div class="flex flex-col">
          <label for="text" class="mb-1 text-sm font-medium text-pink-200">Text</label>
          <input
            type="text"
            name="text"
            id="text"
            placeholder="Enter Text"
            class="px-4 py-2 rounded-md border border-pink-400/40 bg-purple-950 text-white focus:outline-none focus:ring-2 focus:ring-pink-400"
            v-model="text"
          />
        </div>
        <div class="flex flex-col">
          <label for="amt" class="mb-1 text-sm font-medium text-pink-200">Amount</label>
          <input
            type="text"
            name="amt"
            id="amt"
            placeholder="Enter Amount"
            class="px-4 py-2 rounded-md border border-pink-400/40 bg-purple-950 text-white focus:outline-none focus:ring-2 focus:ring-pink-400"
            v-model="cost"
          />
        </div>
      </div>
      <div class="flex gap-5">
      <button
        type="submit"
        class="w-1/2 cursor-pointer px-6 py-2 bg-pink-600 text-white font-semibold rounded-md hover:bg-pink-700 transition"
        @click="addIncome"
      >
        Add Income
      </button>
      <button
        type="submit"
        class="w-1/2 cursor-pointer px-6 py-2 bg-pink-600 text-white font-semibold rounded-md hover:bg-pink-700 transition"
        @click="addExpense"
      >
        Add Expense
      </button>
      </div> 
    </form>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { useToast } from "vue-toastification";

const text = ref('');
const cost = ref('');

const toast = useToast();
const emit = defineEmits(['transactionSubmit']);

const addIncome = () => {
  if (!text.value && !cost.value) {
    toast.error("Both fields must be filled!");
    return;
  } else if (!text.value) {
    toast.error("Text field cannot be empty!");
    return;
  } else if (!cost.value) {
    toast.error("Amount field cannot be empty!");
    return;
  }
  else if(isNaN(cost.value)){
    toast.error("Amount must contain Numeric Value!");
    return;
  }
  const date=new Date();
  const day=date.getDate();
  const month=date.getMonth()+1;
  const year=date.getFullYear();
  const today=day+"-"+month+"-"+year;

  const transactionData = {
    text: text.value,
    cost: parseFloat(cost.value),
    date: today
  };
  emit('transactionSubmit', transactionData);
  text.value = '';
  cost.value = '';
};
const addExpense = () => {
  if (!text.value && !cost.value) {
    toast.error("Both fields must be filled!");
    return;
  } else if (!text.value) {
    toast.error("Text field cannot be empty!");
    return;
  } else if (!cost.value) {
    toast.error("Amount field cannot be empty!");
    return;
  }
  else if(isNaN(cost.value)){
    toast.error("Amount must contain Numeric Value!");
    return;
  }
  const date=new Date();
  const day=date.getDate();
  const month=date.getMonth()+1;
  const year=date.getFullYear();
  const today=day+"-"+month+"-"+year;
  // alert(today);
  const transactionData = {
    text: text.value,
    cost: parseFloat(cost.value*(-1)),
    date: today,
  };
  emit('transactionSubmit', transactionData);
  text.value = '';
  cost.value = '';
};
</script>

<style scoped>
</style>
