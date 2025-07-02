<script setup>
  import NavBar from './components/NavBar.vue';
  import Balance from './components/Balance.vue';
  import IncomeExpenses from './components/IncomeExpenses.vue';
  import AddTransaction from './components/AddTransaction.vue';
  import TransactionHistory from './components/TransactionHistory.vue';

  import {ref,computed} from 'vue';
  const transactions=ref([
    {
        id:1,
        text:"Food",
        cost:-200,
    },
    {
        id:2,
        text:"oil",
        cost:-500,
    },
    {
        id:3,
        text:"tusn",
        cost:1000,
    },
    {
        id:4,
        text:"salary",
        cost:50000,
    },
]);
const balance=computed(()=>{
    return transactions.value.reduce((acc,t)=>{
        return acc+t.cost
    },0)
})
const income=computed(()=>{
  return transactions.value
  .filter((transaction)=> transaction.cost>=0)
  .reduce((acc,t)=>{
    return acc+t.cost
  },0)
})
const expenses=computed(()=>{
  return transactions.value
  .filter((transaction)=>transaction.cost<0)
  .reduce((acc,t)=>{
    return acc+t.cost
  },0)
})
</script>

<template>
  <div class=" bg-[var(--color-bg-dark)] text-white flex flex-col items-center md:p-0 pl-2 pr-2">
    <div class="xl:w-[50%] lg:w-[60%] md:w-[70%] w-full mt-2 mb-2">
      <div>
        <NavBar :theme="theme"/>
      </div>
      <div class="w-full bg-[var(--color-bg-secondary-dark)] mt-2 p-4">
        <Balance :balance="balance"/>
        <IncomeExpenses :income="income" :expenses="expenses"/>
        <TransactionHistory :transactions="transactions"/> 
        <AddTransaction/>
      </div>
    </div>
  </div>
</template>

<style scoped>

</style>
