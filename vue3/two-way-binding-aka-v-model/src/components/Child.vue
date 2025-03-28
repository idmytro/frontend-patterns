<!-- https://vuejs.org/guide/components/v-model.html -->
<script setup>
const model = defineModel()

function update() {
  model.value++
}
</script>

<template>
  <div>Child model is: {{ model }}</div>
  <button @click="update">
    Increment
  </button>
</template>
