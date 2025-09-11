<script lang="ts">
  import favicon from "$lib/assets/favicon.svg";
  import { ModeWatcher } from "mode-watcher";
  import "@fontsource-variable/manrope";

  let { children } = $props();
  import "../app.css";
  import "../main.css";
</script>

<svelte:head>
  <title>adi panda</title>
  <link rel="icon" href={favicon} />
</svelte:head>

<ModeWatcher defaultMode="dark" />
{@render children?.()}
