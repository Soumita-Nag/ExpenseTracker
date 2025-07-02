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
    },
    data(){
      return{
        theme:"light",
      }
    }
  }
</script>

<template>
  <div class=" bg-[var(--color-bg-dark)] text-white flex flex-col items-center md:p-0 pl-2 pr-2">
    <div class="xl:w-[60%] lg:w-[70%] md:w-[80%] w-full mt-2">
      <div>
        <NavBar :theme="theme"/>
      </div>
      <div class="w-full bg-[var(--color-bg-secondary-dark)] mt-2 p-4">
        <Balance/>
        <IncomeExpenses/>
        <AddTransaction/>
        <TransactionHistory/> 
      </div>
    </div>
  </div>
</template>

<style scoped>

</style>
