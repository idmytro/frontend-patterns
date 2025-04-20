<script lang="ts">
  import { onMount } from 'svelte'

  import { replaceState } from '$app/navigation'
  import { page } from '$app/stores'

  import { values } from './ui/constants'
  import Radio from './ui/Radio.svelte'

  const hashValues = values.slice(1)
  let selected: string = values[0]

  function handleRadioChange (event: CustomEvent<string>) {
    const value = event.detail
    if (!values.includes(value)) return
    selected = value

    const { pathname } = $page.url

    if (hashValues.includes(value)) {
      // or pushState
      replaceState(`${pathname}#${selected}`, {})
    }
    else {
      replaceState(pathname, {})
    }
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

<div>
  <Radio {selected} on:change={handleRadioChange} />
</div>
