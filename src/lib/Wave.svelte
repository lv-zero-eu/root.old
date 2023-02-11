<i class="wave"><slot /></i>

<style>
  .wave {
    animation-name: wave-animation; /* Refers to the name of your @keyframes element below */
    animation-duration: 3s; /* Change to speed up or slow down */
    animation-iteration-count: infinite; /* Never stop waving :) */
    transform-origin: 70% 70%; /* Pivot around the bottom-left palm */
    display: inline-block;
  }
  @keyframes wave-animation {
    0% {
      transform: rotate(0deg);
    }
    7% {
      transform: rotate(14deg);
    }
    17% {
      transform: rotate(-8deg);
    }
    27% {
      transform: rotate(14deg);
    }
    37% {
      transform: rotate(-4deg);
    }
    47% {
      transform: rotate(10deg);
    }
    57% {
      transform: rotate(0deg);
    }
    100% {
      transform: rotate(0deg);
    }
  }
</style>
