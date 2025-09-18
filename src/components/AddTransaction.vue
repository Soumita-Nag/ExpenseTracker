<template>
  <div
    class="mx-auto mt-5 p-6 bg-gradient-to-br from-purple-900 via-violet-800 to-pink-700 shadow-md rounded-xl transition-all duration-300 border border-pink-400/30 max-w-3xl"
  >
    <div class="mb-6">
      <h3 class="text-2xl font-semibold text-white pb-2 border-b border-pink-300">
        Add New Transaction
      </h3>
    </div>

    <form @submit.prevent class="space-y-6 w-full">
      <div class="flex flex-wrap gap-4 items-end">
        <div class="flex flex-col flex-1 min-w-[200px]">
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

        <div class="flex flex-col flex-1 min-w-[200px]">
          <label for="amt" class="mb-1 text-sm font-medium text-pink-200">Amount</label>
          <input
            type="text"
            name="amt"
            id="amt"
            placeholder="Enter Amount"
            class="px-4 py-2 rounded-md border border-pink-400/40 bg-purple-950 text-white focus:outline-none focus:ring-2 focus:ring-pink-400"
            v-model="cost"
            inputmode="numeric"
          />
        </div>

        <div class="flex items-center">
          <div class="relative">
            <button
              type="button"
              class="p-2 bg-purple-950 rounded-md hover:bg-purple-800 text-white"
              @click="toggleDateInput"
            >
              <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none"
                viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                  d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z" />
              </svg>
            </button>

            <input
              v-show="showDateInput"
              type="date"
              name="date"
              id="date"
              class="absolute top-10 left-0 px-4 py-2 rounded-md border border-pink-400/40 bg-purple-950 text-white focus:outline-none focus:ring-2 focus:ring-pink-400"
              v-model="today"
            />
          </div>
        </div>
      </div>

      <div class="flex gap-5 mt-4">
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
import { ref, onMounted } from 'vue'
import { useToast } from 'vue-toastification'

const text = ref('')
const cost = ref('')
const today = ref('')
const showDateInput = ref(false)

const toast = useToast()
const emit = defineEmits(['transactionSubmit'])

const calcDate = () => {
  const date = new Date()
  const year = date.getFullYear()
  const month = (date.getMonth() + 1).toString().padStart(2, '0')
  const day = date.getDate().toString().padStart(2, '0')
  today.value = `${year}-${month}-${day}`
}

const toggleDateInput = () => {
  showDateInput.value = !showDateInput.value
}

const addIncome = () => {
  if (!text.value && !cost.value) {
    toast.error('Both fields must be filled!')
    return
  } else if (!text.value) {
    toast.error('Text field cannot be empty!')
    return
  } else if (!cost.value) {
    toast.error('Amount field cannot be empty!')
    return
  } else if (isNaN(cost.value)) {
    toast.error('Amount must contain Numeric Value!')
    return
  }

  const transactionData = {
    text: text.value,
    cost: parseFloat(cost.value),
    date: today.value,
  }

  emit('transactionSubmit', transactionData)
  text.value = ''
  cost.value = ''
}

const addExpense = () => {
  if (!text.value && !cost.value) {
    toast.error('Both fields must be filled!')
    return
  } else if (!text.value) {
    toast.error('Text field cannot be empty!')
    return
  } else if (!cost.value) {
    toast.error('Amount field cannot be empty!')
    return
  } else if (isNaN(cost.value)) {
    toast.error('Amount must contain Numeric Value!')
    return
  }

  const transactionData = {
    text: text.value,
    cost: parseFloat(cost.value) * -1,
    date: today.value,
  }

  emit('transactionSubmit', transactionData)
  text.value = ''
  cost.value = ''
}

onMounted(() => {
  calcDate()
})
</script>
