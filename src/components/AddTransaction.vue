<template>
  <div class=" mx-auto mt-5 p-6 bg-gray-800 shadow-md rounded-xl transition-all duration-300">
    <div class="mb-6">
      <h3 class="text-2xl font-semibold text-white pb-2 border-b border-gray-600">Add New Transaction</h3>
    </div>

    <form @submit.prevent="onSubmit" class="space-y-6 w-full">
      <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
        <div class="flex flex-col">
          <label for="text" class="mb-1 text-sm font-medium text-gray-300">Text</label>
          <input
            type="text"
            name="text"
            id="text"
            placeholder="Enter Text"
            class="px-4 py-2 rounded-md border border-gray-600 bg-gray-700 text-white focus:outline-none focus:ring-2 focus:ring-indigo-500"
            v-model="text"
          />
        </div>
        <div class="flex flex-col">
          <label for="amt" class="mb-1 text-sm font-medium text-gray-300">Amount</label>
          <input
            type="text"
            name="amt"
            id="amt"
            placeholder="Enter Amount"
            class="px-4 py-2 rounded-md border border-gray-600 bg-gray-700 text-white focus:outline-none focus:ring-2 focus:ring-indigo-500"
            v-model="cost"
          />
        </div>
      </div>

      <!-- <div class="flex items-center gap-4">
        <div class="flex items-center">
          <input
            type="radio"
            id="income"
            value="Income"
            v-model="picked"
            class="text-indigo-600 focus:ring-indigo-500"
          />
          <label for="income" class="ml-2 text-sm text-gray-300">Income</label>
        </div>

        <div class="flex items-center">
          <input
            type="radio"
            id="expenses"
            value="Expenses"
            v-model="picked"
            class="text-indigo-600 focus:ring-indigo-500"
          />
          <label for="expenses" class="ml-2 text-sm text-gray-300">Expenses</label>
        </div>
      </div> -->

      <button
        type="submit"
        class="w-full cursor-pointer px-6 py-2 bg-indigo-600 text-white font-semibold rounded-md hover:bg-indigo-700 transition"
      >
        Add Transaction
      </button>
    </form>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { useToast } from "vue-toastification";

const text=ref('')
const cost=ref('')

const toast=useToast()

const emit=defineEmits(['transactionSubmit'])

const onSubmit=()=>{
  if(!text.value && !cost.value){
    toast.error("Both fields must be filled!");
    return
  }
  else if(!text.value){
    toast.error("Text field cannot be empty!")
    return
  }
  else if(!cost.value){
    toast.error("Cost field cannot be empty!")
    return
  }
  else{
    toast.success("Transaction added successfully")
  }

  const transactionData={
    text:text.value,
    cost:parseFloat(cost.value)
  }
  emit('transactionSubmit',transactionData);
  text.value=''
  cost.value=''
}
</script>

<style scoped>
</style>
