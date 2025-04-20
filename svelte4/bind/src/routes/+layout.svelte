<script>
  import 'virtual:uno.css'

  import { page } from '$app/stores'

  let currentPath
  $: currentPath = $page.url.pathname

  import '../assets/main.css'
</script>

<div id="app">
  <header>
    <nav>
      <a href="/" aria-current={currentPath === '/' ? 'page' : undefined}>Home</a>
      <a href="/bind-input" aria-current={currentPath === '/bind-input' ? 'page' : undefined}>Bind input</a>
      <a href="/bind-radio" aria-current={currentPath === '/bind-radio' ? 'page' : undefined}>Bind radio</a>
      <a href="/bind-radio-hash" aria-current={currentPath === '/bind-radio-hash' ? 'page' : undefined}>Bind radio hash</a>
      <a href="/hash-on-page" aria-current={currentPath === '/hash-on-page' ? 'page' : undefined}>Hash on page</a>
      <a href="/hash-read-on-ui" aria-current={currentPath === '/hash-read-on-ui' ? 'page' : undefined}>Hash read on ui</a>
    </nav>
  </header>
  <slot />
</div>

<style>
header {
  line-height: 1.5;
  max-height: 100vh;
}

nav {
  text-align: left;
  margin-left: -1rem;
  font-size: 0;
  padding: 1rem 0;
}

nav a {
  font-size: 1rem;
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

nav a[aria-current='page'] {
  color: var(--color-text);
}

nav a[aria-current='page']:hover {
  background-color: transparent;
}
</style>
