<script lang="ts">
  import './layout.css'
  import favicon from '$lib/assets/favicon.png'

  let { children } = $props()
</script>

<svelte:head>
  <link rel="icon" href={favicon} />
  <title>gandan</title>

  <meta property="og:title" content="gandan" />
  <meta property="og:description" content="14 y/o dev and designer from korea" />
  <meta property="og:image" content="/banner.png" />
  <meta property="og:type" content="website" />

  <meta name="twitter:card" content="summary_large_image" />
  <meta name="twitter:image" content="/banner.png" />
</svelte:head>
{@render children()}
