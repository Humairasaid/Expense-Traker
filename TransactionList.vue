<template>
  <div>
    <h3>History</h3>
    <ul>
      <li v-for="transaction in transactions" :key="transaction.id" :class="{ minus: transaction.amount < 0, plus: transaction.amount > 0 }">
        {{ transaction.text }}
        <span>${{ transaction.amount }}</span>
        <button @click="$emit('delete-transaction', transaction.id)">x</button>
      </li>
    </ul>
  </div>
</template>

<script setup>
defineProps(['transactions'])
</script>

<style scoped>
ul {
  list-style: none;
  padding: 0;
}
li {
  background: white;
  padding: 10px;
  border-right: 5px solid;
  margin: 10px 0;
  position: relative;
  display: flex;
  justify-content: space-between;
}
.plus {
  border-color: green;
}
.minus {
  border-color: red;
}
button {
  background: red;
  color: white;
  border: none;
  cursor: pointer;
}
</style>