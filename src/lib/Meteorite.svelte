<script lang="ts">
  import { onDestroy, onMount } from "svelte";

  type Options = {
    height: number;
    width: number;
    angle: number;
    start: [number, number];
    stop: [number, number];
  };

  export let options: Options = {
    height: 420,
    width: 20,
    angle: -135,
    start: [-350, -150],
    stop: [150, 350],
  };

  let state = {
    pos: options.start,
    height: options.height,
    transistion: true,
  };

  let intervalIn = undefined;
  let intervalOut = undefined;

  function later(delay) {
    return new Promise(function (resolve) {
      setTimeout(resolve, delay);
    });
  }

  onMount(async () => {
    const animation = async () => {
      await later(10)
      state = {
        pos: options.stop,
        height: 0,
        transistion: true,
      };
      await later(2000);
      state = {
        pos: options.start,
        height: options.height,
        transistion: false,
      };
      animation();
    };
    animation();
  });

  onDestroy(() => {
    clearInterval(intervalIn);
    clearTimeout(intervalOut);
  });
</script>

<div
  class="container"
  style="
  --height-container: {options.height + 'px'}; 
  --width-container: {options.width + 'px'}; 
  --angle-container: {options.angle + 'deg'};
  --height-meteorite: {state.height + 'px'};
  --transition: {state.transistion ? '2s linear' : '0s'};
  top: {state.pos[0] + 'px'};
  right: {state.pos[1] + 'px'};
  "
>
  <div class="metheorite" />
</div>

<style>
  .container {
    transform: rotate(var(--angle-container));
    width: var(--width-container);
    height: var(--height-container);
    position: absolute;
    transition: var(--transition);
    border-radius: calc(var(--width-container) / 2)
      calc(var(--width-container) / 2) 0 0;
    overflow: hidden;
  }
  .metheorite {
    width: 100%;
    height: var(--height-meteorite);
    background: linear-gradient(
      #e9702c 10%,
      #fcf5b3 39.73%,
      rgba(255, 246, 165, 0) 86.97%
    );
    transition: var(--transition);
  }
</style>
