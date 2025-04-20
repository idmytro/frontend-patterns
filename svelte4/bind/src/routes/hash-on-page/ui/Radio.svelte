<script lang="ts">
  import { createEventDispatcher } from 'svelte'
  const dispatch = createEventDispatcher<{ change: string }>()

  import { values } from './constants'

  export let selected: string = values[0]

  function handleChange (event: Event) {
    const target = event.target as HTMLInputElement
    const value = target.value
    if (!values.includes(value)) return
    selected = value
    dispatch('change', value)
  }
</script>

<p>Selected: {selected}</p>

<div class="space-x-3">
  {#each values as v (v)}
    <label class="inline-block">
      <input type="radio" bind:group={selected} value={v} on:change={handleChange} />
      {v}
    </label>
  {/each}
</div>
