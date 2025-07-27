
<template>
  <div class="container">
    <Header />
    <Balance :balance="balance" />
    <IncomeExpense :income="income" :expense="expense" />
    <TransactionList :transactions="transactions" @delete-transaction="deleteTransaction" />
    <AddTransaction @add-transaction="addTransaction" />
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import Header from './components/Header.vue'
import Balance from './components/Balance.vue'
import IncomeExpense from './components/IncomeExpense.vue'
import TransactionList from './components/TransactionList.vue'
import AddTransaction from './components/AddTransaction.vue'

const transactions = ref([
  { id: 1, text: 'Sneakers', amount: -200 },
  { id: 2, text: 'Paycheck', amount: 900 },
  { id: 3, text: 'Food', amount: -100 }
])

const balance = computed(() => transactions.value.reduce((acc, t) => acc + t.amount, 0))
const income = computed(() => transactions.value.filter(t => t.amount > 0).reduce((acc, t) => acc + t.amount, 0))
const expense = computed(() => transactions.value.filter(t => t.amount < 0).reduce((acc, t) => acc + t.amount, 0))

function addTransaction(transaction) {
  transactions.value.push({ id: Date.now(), ...transaction })
}

function deleteTransaction(id) {
  transactions.value = transactions.value.filter(t => t.id !== id)
}
</script>

<style>
.container {
  max-width: 400px;
  margin: 30px auto;
  background: #f5f5f5;
  padding: 20px;
  border-radius: 10px;
  font-family: Arial, sans-serif;
}
</style>
