<script lang="ts">
  import { replaceState } from '$app/navigation'
  import { page } from '$app/stores'

  import { firstValue, hashValues } from './ui/constants'
  import Radio from './ui/Radio.svelte'

  /**
   * Sets the value from event as url hash.
   * First option sets empty hash.
   */
  function handleRadioChange (event: CustomEvent<string>) {
    const newValue = event.detail
    const { pathname, hash } = $page.url
    const hashValue = hash.replace('#', '')
    if (newValue === hashValue) return

    if (hashValues.includes(newValue)) {
      replaceState(`${pathname}#${newValue}`, {})
    }
    else if (newValue === firstValue) {
      replaceState(pathname, {})
    }
  }
</script>

<div>
  <Radio on:change={handleRadioChange} />
</div>
