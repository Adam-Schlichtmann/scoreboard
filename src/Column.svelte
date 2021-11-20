<script>
  export let player;
  export let score;
  $: total = Object.values(score).reduce((a, i) => {
    return a + parseInt(i, 10);
  }, 0);
</script>

<div>
  <input bind:value={player} placeholder="enter your name" />
  <input bind:value={score.feathers} min="0" max="10" />
  <input bind:value={score.bonus} min="0" max="10" />
  <input bind:value={score.endOfRound} min="0" max="10" />
  <input bind:value={score.eggs} min="0" max="10" />
  <input bind:value={score.tucked} min="0" max="10" />
  <input bind:value={score.cached} min="0" max="10" />
  <input disabled bind:value={total} min="0" max="10" />
</div>

<style>
  div {
    display: flex;
    justify-content: center;
    flex-direction: column;
    width: 18%;
  }
</style>
