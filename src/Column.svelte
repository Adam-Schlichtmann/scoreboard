<script>
  export let player;
  export let score;
  $: total = Object.values(score).reduce((a, i) => a + parseInt(i, 10), 0);
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

<!-- 75B8C8 77CBB9 506C64 220C10 -->
<style>
  div {
    display: flex;
    justify-content: center;
    flex-direction: column;
    width: 18%;
  }
  input {
    border-color: #220c10;
    background-color: #75b8c8;
    color: #220c10;
    outline: none;
  }
</style>
