<script lang="ts">
  import { createEventDispatcher } from 'svelte'

  export let value: string = ''
  export let values: string[] = []

  const dispatch = createEventDispatcher<{ update: string }>()

  function handleChange (event: Event) {
    const target = event.target as HTMLInputElement
    dispatch('update', target.value)
  }
</script>

<h2>Child Component</h2>

<div class="space-x-3">
  {#each values as v (v)}
    <label class="inline-block">
      <input type="radio" bind:group={value} value={v} on:change={handleChange} />
      {v}
    </label>
  {/each}
</div>

<p>Selected in Child: {value}</p>
