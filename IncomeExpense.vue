<template>
  <div class="inc-exp-container">
    <div>
      <h4>INCOME</h4>
      <p class="plus">+${{ income }}</p>
    </div>
    <div>
      <h4>EXPENSE</h4>
      <p class="minus">-${{ Math.abs(expense) }}</p>
    </div>
  </div>
</template>

<script setup>
defineProps(['income', 'expense'])
</script>

<style scoped>
.inc-exp-container {
  display: flex;
  justify-content: space-between;
  margin: 20px 0;
  padding: 10px;
  background: white;
  border-radius: 5px;
}
.plus {
  color: green;
}
.minus {
  color: red;
}
</style>