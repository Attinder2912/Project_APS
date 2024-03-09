<template>
  <Header></Header>
  <div class="container">
    <Balance></Balance>
    <IncomeExpense></IncomeExpense>
    <TransitionList :transactions="transactions"></TransitionList>
    <AddTransaction></AddTransaction>
  </div>
</template>

<script setup>
  import Header from './components/Header.vue';
  import Balance from './components/Balance.vue';
  import IncomeExpense from './components/IncomeExpense.vue';
  import TransitionList from './components/TransactionList.vue'; // Corrected import path
  import AddTransaction from './components/AddTransaction.vue'; // Corrected import path
  import { ref } from 'vue';

  const transactions = ref([
    { id: 1, text: 'Flower', amount: -19.99 },
    { id: 2, text: 'Salary', amount: -299.97 },
    { id: 3, text: 'Book', amount: -10 },
    { id: 4, text: 'Camera', amount: 150 },
  ]);
</script>

<!-- <script>
  import Header from './components/Header.vue';
  import Balance from './components/Balance.vue';
  import IncomeExpense from './components/IncomeExpense.vue';
  import TransitionList from './components/TransistionList.vue';
  import AddTransaction from './components/AddTransistion.vue';

  export default{
    components:{
      Header,Balance,IncomeExpense,TransitionList,AddTransaction
    },
  };
</script> -->