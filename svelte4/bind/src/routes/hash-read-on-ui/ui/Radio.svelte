<script lang="ts">
  import { createEventDispatcher, onMount } from 'svelte'

  import { page } from '$app/stores'

  import { allValues, hashValues, firstValue } from './constants'

  let selected: string = firstValue

  const dispatch = createEventDispatcher<{ change: string }>()

  function handleChange (event: Event) {
    const target = event.target as HTMLInputElement
    const value = target.value
    if (!allValues.includes(value)) return
    selected = value
    dispatch('change', value)
  }

  function initHashFromPath () {
    // const hash = window.location.hash.replace('#', '')
    const hash = $page.url.hash.replace('#', '')
    if (hashValues.includes(hash)) {
      selected = hash
    }
  }

  onMount(initHashFromPath)
</script>

<p>Selected: {selected}</p>

<div class="space-x-3">
  {#each allValues as v (v)}
    <label class="inline-block">
      <input type="radio" bind:group={selected} value={v} on:change={handleChange} />
      {v}
    </label>
  {/each}
</div>
