<script lang="ts">
  import {} from "svelte/easing";
  import Building from "./lib/Building.svelte";
  import Wave from "./lib/Wave.svelte";
</script>

<main>
  <h1>
    <Wave>🖖</Wave>
    <div class="">You lost your way👨‍🦯</div>
  </h1>
  <div class="buildings">
    <Building />
    <Building height={6} width={4} />
    <Building />
  </div>
</main>

<style>
  main {
    width: 100%;
    height: 100%;
    background: linear-gradient(180deg, #000611 0.01%, #002e69 100%);
    mix-blend-mode: normal;
    text-align: center;
    display: flex;
    flex-direction: column;
    justify-content: center;
  }
  main h1 {
    margin-top: calc(50vh - 40px *2);
    font-weight: 700;
    font-size: 40px;
  }
  main .buildings {
    margin-top: auto;
    margin-bottom: 50px;
    display: flex;
    width: 100%;
    justify-content: center;
    align-items: flex-end;
  }
</style>
