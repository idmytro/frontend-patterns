<script setup lang="ts">
import { ref } from 'vue'

import Child from './Child.vue'

const countModel = ref(0)
</script>

<template>
  <div>
    <p>Parent bound modelValue is: {{ countModel }}</p>
    <Child
      :modelValue="countModel"
      @update:modelValue="countModel = $event"
    />
  </div>
</template>
