<template>
  <div>
    <h4>Your Balance</h4>
    <h1>${{ balance }}</h1>
  </div>
</template>

<script setup>
defineProps(['balance'])
</script>

<style scoped>
h1 {
  margin: 0;
}
</style>