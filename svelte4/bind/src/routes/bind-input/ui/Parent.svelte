<!-- Parent.svelte -->
<script lang="ts">
  import Child from './Child.svelte'

  let name: string = 'John Doe'

  function updateName (event: CustomEvent<string>) {
    name = event.detail
  }
</script>

<h1>Parent Component</h1>
<p>Parent Name: {name}</p>

<Child bind:value={name} on:update={updateName} />
