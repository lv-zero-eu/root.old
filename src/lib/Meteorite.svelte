<script lang="ts">
  export let height = 420;
  export let width = 20;
  export let angle = -135;
</script>

<div
  style="
  --height-meteorite: {height + 'px'}; 
  --width-meteorite: {width + 'px'}; 
  --angle-meteorite: {angle + 'deg'};
  "
/>

<style>
  div {
    top: -350px;
    right: -150px;
    position: absolute;
    transform: rotate(var(--angle-meteorite));
    display: block;
    width: var(--width-meteorite);
    height: var(--height-meteorite);
    background: linear-gradient(
      #e9702c 10%,
      #fcf5b3 39.73%,
      rgba(255, 246, 165, 0) 86.97%
    );
    border-radius: calc(var(--width-meteorite) / 2)
      calc(var(--width-meteorite) / 2) 0 0;
  }
</style>
