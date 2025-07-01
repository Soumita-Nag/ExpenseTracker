<script>
  import NavBar from './components/NavBar.vue';
  import Balance from './components/Balance.vue';
  import IncomeExpenses from './components/IncomeExpenses.vue';
  import AddTransaction from './components/AddTransaction.vue';
  import TransactionHistory from './components/TransactionHistory.vue';
  export default{
    components:{
      NavBar,
      Balance,
      IncomeExpenses,
      AddTransaction,
      TransactionHistory,
    }
  }
</script>

<template>
  <div class=" bg-[var(--color-bg)] text-white h-[100vh]">
    <NavBar/>
    <Balance/>
    <IncomeExpenses/>
    <AddTransaction/>
    <TransactionHistory/> 
  </div>
</template>

<style scoped>

</style>
