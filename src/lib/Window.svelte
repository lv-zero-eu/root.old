<script lang="ts">
  import { onDestroy } from "svelte";

  export let id: number;
  export let light = Math.random() > 0.20;
  export let animate = light && Math.random() < 0.4;

  let interval: number;

  if (animate) {
    setTimeout(() => {
      light = !light;
      interval = setInterval(() => {
        light = !light;
      }, 4000 + Math.random() * 1000);
    }, Math.random() * 5000);
  }

  onDestroy(() => {
    clearInterval(interval);
  });
</script>

<i class={`cell cell-${id} cell-${light ? "on" : "off"}`} />

<style>
  .cell {
    display: block;
    width: 25px;
    height: 25px;
    transition: 1s ease-in-out;
  }
  .cell.cell-on {
    background: #dcdd9e;
  }
  .cell.cell-off {
    background: #002960;
  }
</style>
