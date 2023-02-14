<script lang="ts">
  import { onDestroy } from "svelte";

  export let id: number;
  export let light = Math.random() > 0.15;
  export let animate = light && Math.random() > 0.3;

  let interval: number;

  if (animate) {
    setTimeout(() => {
      interval = setInterval(() => {
        light = !light;
      }, 4000 + Math.random() * 10000);
    }, Math.random() * 1000);
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
