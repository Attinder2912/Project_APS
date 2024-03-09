<template>
  <Header></Header>
  <div class="container">
    <Balance :total="total"></Balance>
    <IncomeExpense :income="+income" :expenses="+expenses"></IncomeExpense>
    <TransitionList :transactions="transactions"></TransitionList>
    <AddTransaction @transactionSubmitted="handleTrasnactionSubmitted"></AddTransaction>
  </div>
</template>

<script setup>
  import Header from './components/Header.vue';
  import Balance from './components/Balance.vue';
  import IncomeExpense from './components/IncomeExpense.vue';
  import TransitionList from './components/TransactionList.vue'; // Corrected import path
  import AddTransaction from './components/AddTransaction.vue'; // Corrected import path
  import { ref ,computed} from 'vue';

// ref to make reactive things
  const transactions = ref([
    { id: 1, text: 'Flower', amount: -19.99 },
    { id: 2, text: 'Salary', amount: 299.97 },
    { id: 3, text: 'Book', amount: -10 },
    { id: 4, text: 'Camera', amount: 150 },
  ]);
//get total
  const total=computed(()=>{
    return transactions.value.reduce((acc,transactions)=>{
    return acc + transactions.amount;
  },0);
});
//get income
const income=computed(()=>{
  return transactions.value
  .filter((transaction)=>transaction.amount>0)
  .reduce((acc,transaction)=>{
    return acc+transaction.amount
  }, 0)
  .toFixed(2);
});
//get expense
const expenses=computed(()=>{
  return transactions.value
  .filter((transaction)=>transaction.amount<0)
  .reduce((acc,transaction)=>{
    return acc+transaction.amount
  }, 0)
  .toFixed(2);
});

//Add transaction
const handleTrasnactionSubmitted = (transactionData)=>{
 // console.log(transactionData);
 transactions.value.push({
  id:generateUniqueId(),
  text:transactionData.text,
  amoutn:transactionData.amount
 });
 //console.log(generateUniqueId());
};
//generate Unique id
const generateUniqueId=()=>{
  return Math.floor(Math.random()*1000000);
}
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