<script lang="ts">
  import favicon from "$lib/assets/favicon.svg";
  import { ModeWatcher } from "mode-watcher";

  let { children } = $props();
  import "../app.css";
</script>

<svelte:head>
  <link rel="icon" href={favicon} />
</svelte:head>

<ModeWatcher defaultMode="dark" />
{@render children?.()}
