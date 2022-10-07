<template>
  <div class="container">
    <h5>Scheduled Transactions</h5>
    <table class="table">
    <thead>
      <tr>
        <th>Account</th>
        <th>Date</th>
        <th>Payee</th>
        <th>Category</th>
        <th>Memo</th>
        <th>Amount</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="scheduled_transaction in scheduledTransactions" v-bind:key="scheduled_transaction.id">
        <template v-if="scheduled_transaction.date_next <= '2022-12-01'">
        <td>{{scheduled_transaction.account_name}}</td>
        <td>{{scheduled_transaction.date_next}}</td>
        <td>{{scheduled_transaction.payee_name}}</td>
        <td>{{scheduled_transaction.category_name}}</td>
        <td>{{scheduled_transaction.memo}}</td>
        <td>{{fakeAmount(convertMilliUnitsToCurrencyAmount(scheduled_transaction.amount).toFixed(2))}}</td>
      </template>

      </tr>
    </tbody>
    </table>
  </div>
</template>

<script>
// Import utils from YNAB
import {utils} from 'ynab';

export default {
  props: ['scheduledTransactions'],
  methods: {
    // Now we can make this method available to our template
    // So we can format this milliunits in the correct currency format
    convertMilliUnitsToCurrencyAmount: utils.convertMilliUnitsToCurrencyAmount,
    filterDates(date) {
      return this.$options.filters.mm(date) === "10";
    },
    fakeAmount(amount) {
      if (amount < -100) {
        return (-100.00)
      }
      else {return amount}
    }
  }
}
</script>
