<script setup lang="ts">
import { ref } from 'vue'

import Child from './Child.vue'

const countModel = ref(0)
</script>

<template>
  <div>
    <p>Parent bound v-model is: {{ countModel }}</p>
    <Child v-model="countModel" />
  </div>
</template>
