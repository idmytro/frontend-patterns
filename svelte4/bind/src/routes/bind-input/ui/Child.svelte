<script lang="ts">
  import { createEventDispatcher } from 'svelte'

  /** Prop received from the parent */
  export let value = ''
  const dispatch = createEventDispatcher<{ update: string }>()

  function handleInput (event: Event) {
    const target = event.target as HTMLInputElement
    dispatch('update', target.value)
  }
</script>

<h2>Child Component</h2>
<input type="text" bind:value={value} on:input={handleInput} />
<p>Child Name: {value}</p>
