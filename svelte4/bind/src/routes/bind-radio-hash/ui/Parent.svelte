<script lang="ts">
  import { onMount } from 'svelte'

  import Child from './Child.svelte'

  const values: string[] = ['first', 'second', 'third'] as const
  const hashValues = values.slice(1)

  let selected: string = 'first' satisfies typeof values[number]

  function updateSelection (event: CustomEvent<string>) {
    const value = event.detail
    if (!values.includes(value)) return
    selected = value

    if (hashValues.includes(value)) {
      // window.location.hash = value // Update the URL hash
      // or replaceState
      window.history.pushState({}, '', `#${value}`) // Update the URL hash
    }
    else {
      window.history.pushState({}, '', window.location.pathname)
    }
  }

  onMount(() => {
    const hash = window.location.hash.replace('#', '')
    if (values.includes(hash)) {
      selected = hash
    }
  })
</script>

<h1>Parent Component</h1>
<p>Selected: {selected}</p>

<Child bind:value={selected} {values} on:update={updateSelection} />
