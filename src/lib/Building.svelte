<script lang="ts">
  export let width = 3;
  export let height = 3;

  const windows = Array(height).fill(
    Array(width).fill((w) => {
      {
      }
    })
  );

  console.log(windows);
</script>

<div class="building">
  <div class="windows">
    {#each windows as _, h}
      <div class={`row row-${h}`}>
        {#each windows[h] as _, w}
          <div class={`cell cell-${h * windows.length + w}`} />
        {/each}
      </div>
    {/each}
  </div>
</div>

<style>
  .windows {
    width: fit-content;
    background: rgba(0, 0, 0, 0.6);
    padding: 25px 15px;
    display: flex;
    flex-direction: column;
    gap: 10px;
  }
  .row {
    display: flex;
    flex-direction: row;
    gap: 12px;
  }
  .cell {
    display: block;
    width: 25px;
    height: 25px;
    background: #dcdd9e;
  }

  .row:nth-child(1) > .cell:nth-child(2) {
    background-color: #002960;
  }
</style>
