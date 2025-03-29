<script lang="ts">
  import { onMount } from 'svelte'

  const values: string[] = ['first', 'second', 'third'] as const
  const hashValues = values.slice(1)

  let selected: string = 'first' satisfies typeof values[number]

  function handleChange (event: Event) {
    const target = event.target as HTMLInputElement
    const value = target.value
    if (!values.includes(value)) return
    selected = value

    if (hashValues.includes(value)) {
      window.history.pushState({}, '', `#${value}`) // Update the URL hash
    }
    else {
      window.history.pushState({}, '', window.location.pathname)
    }
  }

  function initHashFromPath () {
    const hash = window.location.hash.replace('#', '')
    if (values.includes(hash)) {
      selected = hash
    }
  }

  onMount(initHashFromPath)
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
