<script lang="ts">
  import Window from "./Window.svelte";

  export let width = 3;
  export let height = 3;
  export let roofLight = true;

  const windows = Array(height).fill(Array(width).fill({}));
</script>

<div class="building">
  <div class="roof">
    {#if roofLight}
      <i class="light" /> <i class="light" />
    {/if}
  </div>
  <div class="windows">
    {#each windows as _, h}
      <div class={`row row-${h}`}>
        {#each windows[h] as _, w}
          <Window id={h * windows.length + w} />
        {/each}
      </div>
    {/each}
  </div>
</div>

<style>
  @media (max-width: 480px) {
    .building {
      zoom: calc(0.75);
    }
  }
  .roof {
    margin-left: 7.5%;
    width: 85%;
    height: 50px;
    display: flex;
    justify-content: space-between;
    align-items: flex-end;
  }
  .roof .light {
    display: block;
    width: 10px;
    height: 10px;
    animation-name: pulse;
    animation-duration: 3s;
    animation-timing-function: ease-in-out;
    animation-direction: alternate;
    animation-iteration-count: infinite;
    animation-play-state: running;
  }
  .windows {
    width: fit-content;
    background: rgba(0, 0, 0, 0.6);
    padding: 25px 15px;
    display: flex;
    flex-direction: column;
    gap: 15px;
  }
  .row {
    display: flex;
    flex-direction: row;
    gap: 18px;
  }

  @keyframes pulse {
    0% {
      background-color: rgb(185, 9, 9);
    }
    100% {
      background-color: rgba(147, 11, 11, 0.7);
    }
  }
</style>
