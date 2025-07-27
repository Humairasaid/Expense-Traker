<template>
  <div>
    <h3>Add new transaction</h3>
    <form @submit.prevent="handleSubmit">
      <div>
        <label>Text</label>
        <input v-model="text" type="text" placeholder="Enter text..." />
      </div>
      <div>
        <label>Amount<br />(negative - expense, positive - income)</label>
        <input v-model.number="amount" type="number" placeholder="Enter amount..." />
      </div>
      <button type="submit">Add transaction</button>
    </form>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const text = ref('')
const amount = ref(0)

const emit = defineEmits(['add-transaction'])

function handleSubmit() {
  if (!text.value || !amount.value) return

  emit('add-transaction', {
    text: text.value,
    amount: amount.value
  })

  text.value = ''
  amount.value = 0
}
</script>

<style scoped>
input {
  width: 100%;
  padding: 8px;
  margin: 6px 0 12px;
}
button {
  width: 100%;
  padding: 10px;
  background: purple;
  color: white;
  border: none;
  border-radius: 5px;
}
</style>