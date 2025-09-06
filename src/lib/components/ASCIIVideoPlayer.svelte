<script lang="ts">
  import { onMount, onDestroy } from "svelte";
  import videoUrl from "$lib/assets/video_2.txt?url";

  export let fps: number = 10; // frames per second

  // State variables
  let frames: string[] = [];
  let currentFrame: number = 0;
  let intervalId: number | null = null;
  let videoContent: string = "";

  // Reactive statements
  $: frameDelay = 1000 / fps; // milliseconds between frames

  // Parse the ASCII video content
  function parseASCIIVideo(content: string): string[] {
    if (!content) return [];

    // Split by double newlines (empty lines) to separate frames
    const frameStrings = content.split(/\n\s*\n/);

    // Filter out empty frames and trim whitespace
    return frameStrings
      .map((frame) => frame.trim())
      .filter((frame) => frame.length > 0);
  }

  // Start playing the animation
  function play(): void {
    if (frames.length === 0) return;

    intervalId = setInterval(() => {
      currentFrame = (currentFrame + 1) % frames.length; // Loop automatically
    }, frameDelay);
  }

  // Stop the animation
  function stop(): void {
    if (intervalId) {
      clearInterval(intervalId);
      intervalId = null;
    }
  }

  // Watch for content changes
  $: {
    frames = parseASCIIVideo(videoContent);
    currentFrame = 0;

    // Restart animation when content changes
    stop();
    if (frames.length > 0) {
      play();
    }
  }

  // Handle fps changes during playback
  $: if (intervalId && frames.length > 0) {
    stop();
    play();
  }

  // Fetch video content
  async function loadVideoContent() {
    try {
      const response = await fetch(videoUrl);
      videoContent = await response.text();
    } catch (error) {
      console.error("Failed to load video content:", error);
      videoContent = "";
    }
  }

  // Auto-start on mount
  onMount(async () => {
    await loadVideoContent();
    if (frames.length > 0) {
      play();
    }
  });

  // Cleanup on component destroy
  onDestroy(() => {
    stop();
  });
</script>

<div class="ascii-video-player">
  {#if frames.length > 0}
    <pre class="ascii-frame">{(frames[currentFrame] || "").replace(
        /\./g,
        " ",
      )}</pre>
  {:else}
    <div class="placeholder"></div>
  {/if}
</div>

<style>
  .ascii-video-player {
    display: inline-block;
  }

  .ascii-frame {
    font-family: "Courier New", monospace;
    font-size: 12px;
    line-height: 1.1;
    margin: 0;
    padding: 20px;
    white-space: pre;
    border-radius: 5px;
    overflow: visible;
  }

  .placeholder {
    color: #666;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
      sans-serif;
    padding: 20px;
    text-align: center;
  }
</style>
