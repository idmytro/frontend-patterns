<script lang="ts">
  import Child from './Child.svelte'

  let selected: string = 'first'
  const values: string[] = ['first', 'second', 'third']

  function updateSelection (event: CustomEvent<string>) {
    selected = event.detail
  }
</script>

<h1>Parent Component</h1>
<p>Selected: {selected}</p>

<Child bind:value={selected} {values} on:update={updateSelection} />
