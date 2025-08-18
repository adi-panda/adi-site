<script lang="ts">
  import { onMount } from "svelte";
  import { Button } from "$lib/components/ui/button/index.js";
  import headshot from "$lib/assets/Aditya_Panda_Headshot.jpeg";

  let count: number = 0;

  onMount(() => {
    console.log("Mounted");
    const name: string = "Adi Panda";
    console.log(name);
  });
</script>

<main class="flex flex-col items-center justify-center h-screen">
  <div
    class="flex flex-col items-start justify-center gap-2 w-full px-8 md:w-1/2 lg:w-2/7"
  >
    <img src={headshot} alt="Adi Panda" class="rounded-md" />
    <h1 class="text-xl font-bold">Adi Panda</h1>

    <span class="text-sm text-muted-foreground">
      Hey! I'm Adi. I'm an engineer and studying CS at UT Austin, but I
      generally just like making stuff. Here's some stuff I worked on:
    </span>
    <ul class="text-sm text-muted-foreground list-disc ml-4">
      <li>Built video datasets for leading AI research labs at Sieve.</li>
      <li>
        Founded toona, a platform for creating animated stories, and scaled it
        to 100k+ users.
      </li>
      <li>Worked on custom creative tools for leading studios at Hyperbrew.</li>
      <li>Made a YouTube channel with over 20k subscribers.</li>
    </ul>
    <Button
      onclick={() => count++}
      variant={"outline"}
      class="hover:cursor-pointer rounded-full">Click</Button
    >
  </div>
</main>
