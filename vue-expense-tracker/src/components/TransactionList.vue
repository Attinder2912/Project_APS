<template>
    <h3>History</h3>
    <ul id="list" class="list">
      <li v-for="transaction in transactions" :key="transaction.id" :class="transaction.amount < 0 ? 'minus' : 'plus'">
        {{ transaction.text }}<span>{{ transaction.amount }}</span>
        <button class="delete-btn">x</button>
      </li>
    </ul>
  </template>
  
  <script setup>
  import { defineProps } from 'vue';
  
  const props = defineProps({
    transactions: {
      type: Array,
      required: true,
    },
  });
  </script>
  
<!--taking this to app.vue to call as a compostion API-->
<!--here below is three ways to define 1. script setup 2. data() 3. setup()-->


<!-- <script>
//option API
// export default{
//     // 1.
//     // data(){
//     //     return{
//     //         transaction:[
//     //             {id:1, text:'Flower',amount:-19.99},
//     //             {id:2, text:'salary',amount:-299.97},
//     //             {id:3, text:'Book',amount:-10},
//     //             {id:4, text:'Camera',amount:150},
//     //         ]
//     //     }
//     // 2.
//     setup(){
//         const transaction = [
//                 {id:1, text:'Flower',amount:-19.99},
//                 {id:2, text:'salary',amount:-299.97},
//                 {id:3, text:'Book',amount:-10},
//                 {id:4, text:'Camera',amount:150},
//         ];
//         return{
//             transaction,
//         };
//     },
// };
</script> -->
