<script setup>
  import NavBar from './components/NavBar.vue';
  // import Balance from './components/Balance.vue';
  import IncomeExpenses from './components/IncomeExpenses.vue';
  import AddTransaction from './components/AddTransaction.vue';
  import TransactionHistory from './components/TransactionHistory.vue';
  import FooterPage from './components/FooterPage.vue'

  import { ref, computed, onMounted } from 'vue';
  import { useToast } from "vue-toastification";

  const toast = useToast();

  onMounted(() => {
    const savedTransactions = JSON.parse(localStorage.getItem('transactions'))
    if (savedTransactions) {
      transactions.value = savedTransactions;
    }
  })

  const updateLocalStorage = () => {
    localStorage.setItem('transactions', JSON.stringify(transactions.value))
  }

  const transactions = ref([]);

  const balance = computed(() => {
    return transactions.value.reduce((acc, t) => acc + t.cost, 0)
  })

  const income = computed(() => {
    return transactions.value
      .filter((transaction) => transaction.cost >= 0)
      .reduce((acc, t) => acc + t.cost, 0)
  })

  const expenses = computed(() => {
    return transactions.value
      .filter((transaction) => transaction.cost < 0)
      .reduce((acc, t) => acc + t.cost, 0)
  })

  const saveTransaction = (transactionData) => {
    transactions.value.push({
      id: generateUniqId(),
      text: transactionData.text,
      cost: transactionData.cost
    })
    toast.success("Transaction added successfully");
    updateLocalStorage();
  }

  const generateUniqId = () => {
    return Math.floor(Math.random() * 100000);
  }

  const deleteTransaction = (id) => {
    transactions.value = transactions.value.filter((t) => t.id != id);
    toast.success('Transaction Deleted')
    updateLocalStorage();
  }
</script>

<template>
  <div class="bg-gradient-to-b from-[#080014] to-[#1e0149] text-white flex flex-col items-center md:p-0 pl-2 pr-2 min-h-screen">
    <div class="xl:w-[50%] lg:w-[60%] md:w-[70%] w-full mt-2 mb-11">
      <div>
        <NavBar />
      </div>
      <div class="w-full bg-purple-950/60 backdrop-blur-md rounded-xl shadow-lg mt-2 p-4 ">
        <!-- <Balance  /> -->
        <IncomeExpenses :balance="balance" :income="income" :expenses="expenses" />
        <AddTransaction @transactionSubmit="saveTransaction" />
        <TransactionHistory :transactions="transactions" @deleteTransaction="deleteTransaction" />
      </div>
    </div>
    <FooterPage/>
  </div>
</template>

<style>
  ::-webkit-scrollbar{
    width: 8px;
  }
  ::-webkit-scrollbar-track{
    background-color: rgb(59, 0, 87);

  }
  ::-webkit-scrollbar-thumb{
    background-color: rgb(255, 0, 174);
    border-radius: 20px;
  }
</style>
