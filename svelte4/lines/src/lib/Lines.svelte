<script lang="ts">
  import { onMount } from 'svelte'

  let start: HTMLElement | null = null
  let end: HTMLElement | null = null

  onMount(() => {
    new window.LeaderLine(start, end, { color: 'grey', size: 2 })
  })
</script>

<div class="h-2000px flex gap-100px">
  <div class="mb-1900px" bind:this={start}>start</div>
  <div class="mt-1900px" bind:this={end}>end</div>
</div>

<h1>H1</h1>

<div class="flex gap-100px">
  <div id="start">start</div>
  <div id="end" class="mt-100px">end</div>
</div>
