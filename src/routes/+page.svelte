<script>
  import { onMount } from 'svelte';
  import ConfettiGenerator from 'confetti-js';

  let confetti;

  onMount(() => {
    confetti = new ConfettiGenerator({ target: 'confetti-canvas' });
  });

  function releaseConfetti() {
    confetti.render();
    setTimeout(() => confetti.clear(), 3000); // stop after 3 seconds
  }
</script>

<style>
  .confetti-canvas {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    pointer-events: none;
    z-index: 9999;
  }
  .center-container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 100vh;
    text-align: center;
  }
  button {
    margin-top: 20px; /* Optional spacing between the text and the button */
  }
</style>

<div class="center-container">
  <h1>Jason Cornell x ESPN</h1>
  <button on:click={releaseConfetti}>Release Confetti</button>
</div>
<canvas id="confetti-canvas" class="confetti-canvas"></canvas>

