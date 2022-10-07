<template>
    <div class="transactions container">
      <h5>Select Transaction Type</h5>
      <div v-for="transactionType in transactionTypes" class="row">
        <a class="col" href="#" @click="selectType(transactionType, $event)">
          {{transactionType}}
        </a>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: ['transactionTypes', 'selectType']
  }
  </script>
  