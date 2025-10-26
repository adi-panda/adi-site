<script>
  import { Button } from "@/lib/components/ui/button";
  import { SunIcon, MoonIcon } from "@lucide/svelte";
  import { toggleMode } from "mode-watcher";
  import AsciiVideoPlayer from "@/lib/components/ASCIIVideoPlayer.svelte";
  import { GithubIcon, TwitterIcon, LinkedinIcon } from "@lucide/svelte";
</script>

<main
  class="h-screen w-full flex items-center justify-start lg:justify-center overflow-x-hidden px-0 lg:px-4 lg:pt-0 pt-12 flex-col lg:flex-row"
>
  <Button
    onclick={toggleMode}
    variant="outline"
    size="icon"
    class="absolute top-4 right-4"
  >
    <SunIcon
      class="h-[1.2rem] w-[1.2rem] rotate-0 scale-100 !transition-all dark:-rotate-90 dark:scale-0"
    />
    <MoonIcon
      class="absolute h-[1.2rem] w-[1.2rem] rotate-90 scale-0 !transition-all dark:rotate-0 dark:scale-100"
    />
    <span class="sr-only">Toggle theme</span>
  </Button>

  <div
    class="flex flex-col items-start justify-center gap-8 px-8 xl:w-[35%] slide-in-from-right"
  >
    <h1 class="text-lg pb-10">adi panda</h1>
    <div class="flex flex-col gap-2 pb-4">
      <!-- <img src={headshot} alt="Adi Panda" class="rounded-md w-[4rem]" /> -->
      <span class="text-xl text-foreground">
        👋 hey! i'm adi, an engineer @ <a
          href="https://krea.ai"
          class="underline">krea</a
        > and studying cs at ut austin. i ❤️ visual computing, ml and consumer products.
      </span>
      <span class="text-xl text-foreground">
        here's some stuff I worked on:
      </span>
    </div>

    <ul class="text-md text-foreground list-disc ml-4 cursor-default">
      <li class="transition-all duration-200 ease-in-out hover:translate-x-2">
        built video datasets for leading AI labs at
        <a href="https://sievedata.com" class="underline">sieve</a>.
      </li>
      <li class="transition-all duration-200 ease-in-out hover:translate-x-2">
        founded <a href="https://toona.io" class="underline">toona</a>, an AI
        animation platform and scaled it to 100k+ users.
      </li>
      <li class="transition-all duration-200 ease-in-out hover:translate-x-2">
        worked on custom creative tools for leading studios at
        <a href="https://hyperbrew.co" class="underline">hyperbrew</a>.
      </li>
      <li class="transition-all duration-200 ease-in-out hover:translate-x-2">
        made a
        <a href="https://youtube.com/@awdii" class="underline"
          >youtube channel</a
        >
        with over 20k subscribers.
      </li>
    </ul>

    <hr class="border-muted-foreground border-t w-full m-0 p-0" />

    <div class="grid grid-cols-3 gap-2 w-full">
      <Button
        class="w-full"
        variant="outline"
        href="https://github.com/adi-panda"
      >
        <GithubIcon /> <span class="hidden md:block">Github</span>
      </Button>
      <Button class="w-full" variant="outline" href="https://x.com/awdii_">
        <TwitterIcon /> <span class="hidden md:block"> Twitter (X)</span>
      </Button>
      <Button
        class="w-full"
        variant="outline"
        href="https://www.linkedin.com/in/adipanda/"
      >
        <LinkedinIcon /> <span class="hidden md:block">LinkedIn</span>
      </Button>
    </div>
  </div>

  <div
    class="slide-in-from-left lg:transform lg:translate-x-12 lg:-translate-y-8 pt-[3rem] w-[40rem] flex items-center justify-center"
  >
    <AsciiVideoPlayer />
  </div>
</main>

<style>
  @keyframes slideInFromRight {
    0% {
      opacity: 0;
      transform: translateX(10%);
    }
    100% {
      opacity: 100;
      transform: translateX(0);
    }
  }
  .slide-in-from-right {
    animation: 0.3s ease-out 0s 1 slideInFromRight;
  }

  @keyframes slideInFromLeft {
    0% {
      opacity: 0;
      transform: translateX(-10%);
    }
    100% {
      opacity: 100;
      transform: translateX(0);
    }
  }
  .slide-in-from-left {
    animation: 0.3s ease-out 0s 1 slideInFromLeft;
  }
</style>
