<script lang="ts">
  type Round = {
    feathers: number;
    bonus: number;
    endOfRound: number;
    eggs: number;
    tucked: number;
    cached: number;
  };
  type Player = { name: string; score: [Round, Round, Round, Round] };
  type Game = [Player, Player, Player, Player, Player];

  const game: Game = [
    {
      name: "",
      score: [
        { feathers: 0, bonus: 0, endOfRound: 0, eggs: 0, tucked: 0, cached: 0 },
        { feathers: 0, bonus: 0, endOfRound: 0, eggs: 0, tucked: 0, cached: 0 },
        { feathers: 0, bonus: 0, endOfRound: 0, eggs: 0, tucked: 0, cached: 0 },
        { feathers: 0, bonus: 0, endOfRound: 0, eggs: 0, tucked: 0, cached: 0 },
      ],
    },
    {
      name: "",
      score: [
        { feathers: 0, bonus: 0, endOfRound: 0, eggs: 0, tucked: 0, cached: 0 },
        { feathers: 0, bonus: 0, endOfRound: 0, eggs: 0, tucked: 0, cached: 0 },
        { feathers: 0, bonus: 0, endOfRound: 0, eggs: 0, tucked: 0, cached: 0 },
        { feathers: 0, bonus: 0, endOfRound: 0, eggs: 0, tucked: 0, cached: 0 },
      ],
    },
    {
      name: "",
      score: [
        { feathers: 0, bonus: 0, endOfRound: 0, eggs: 0, tucked: 0, cached: 0 },
        { feathers: 0, bonus: 0, endOfRound: 0, eggs: 0, tucked: 0, cached: 0 },
        { feathers: 0, bonus: 0, endOfRound: 0, eggs: 0, tucked: 0, cached: 0 },
        { feathers: 0, bonus: 0, endOfRound: 0, eggs: 0, tucked: 0, cached: 0 },
      ],
    },
    {
      name: "",
      score: [
        { feathers: 0, bonus: 0, endOfRound: 0, eggs: 0, tucked: 0, cached: 0 },
        { feathers: 0, bonus: 0, endOfRound: 0, eggs: 0, tucked: 0, cached: 0 },
        { feathers: 0, bonus: 0, endOfRound: 0, eggs: 0, tucked: 0, cached: 0 },
        { feathers: 0, bonus: 0, endOfRound: 0, eggs: 0, tucked: 0, cached: 0 },
      ],
    },
    {
      name: "",
      score: [
        { feathers: 0, bonus: 0, endOfRound: 0, eggs: 0, tucked: 0, cached: 0 },
        { feathers: 0, bonus: 0, endOfRound: 0, eggs: 0, tucked: 0, cached: 0 },
        { feathers: 0, bonus: 0, endOfRound: 0, eggs: 0, tucked: 0, cached: 0 },
        { feathers: 0, bonus: 0, endOfRound: 0, eggs: 0, tucked: 0, cached: 0 },
      ],
    },
  ];
  let round = 0;

  const increment = () => {
    if (round === 3) round = 0;
    else round += 1;
  };
  const decrement = () => {
    if (round === 0) round = 3;
    else round -= 1;
  };
  $: totals = game.map((item) =>
    Object.values(item.score[round]).reduce(
      (innerAcc, innerItem) => innerAcc + innerItem,
      0
    )
  );
</script>

<round>
  <button on:click={decrement}>Previous</button>
  <p>ROUND: {round + 1}</p>
  <button on:click={increment}>Next</button>
</round>
<board>
  <input value="Names" disabled class="label" />
  <input value="Feathers" disabled class="label" />
  <input value="Bonus" disabled class="label" />
  <input value="End of Round Goal" disabled class="label" />
  <input value="Eggs" disabled class="label" />
  <input value="Tucked Cards" disabled class="label" />
  <input value="Cached Food" disabled class="label" />
  <input value="Total" disabled class="label" />
  {#each game as player, i}
    <input bind:value={player.name} placeholder="enter your name" />
    <input bind:value={player.score[round].feathers} type="number" min="0" />
    <input bind:value={player.score[round].bonus} type="number" min="0" />
    <input bind:value={player.score[round].endOfRound} type="number" min="0" />
    <input bind:value={player.score[round].eggs} type="number" min="0" />
    <input bind:value={player.score[round].tucked} type="number" min="0" />
    <input bind:value={player.score[round].cached} type="number" min="0" />
    <input disabled bind:value={totals[i]} type="number" min="0" />
  {/each}
</board>

<style>
  :global(body) {
    margin: 0;
    background-color: #77cbb9;
  }

  round {
    display: flex;
    justify-content: center;
    flex-direction: row;
    align-content: center;
  }

  board {
    display: grid;
    grid-template-columns: repeat(6 1fr);
    grid-template-rows: repeat(8, 1fr);
    grid-column-gap: 10px;
    grid-auto-flow: column;
  }
  .label {
    border-color: #77cbb9;
    background-color: #77cbb9;
    color: #220c10;
    outline: none;
    font-size: large;
  }
  input {
    border-color: #220c10;
    background-color: #75b8c8;
    color: #220c10;
    outline: none;
    font-size: large;
  }
  button {
    background-color: #75b8c8;
    border-color: #75b8c8;
    border-radius: 1em;
    min-width: 150px;
    width: 15%;
    font-size: large;
  }

  button:active,
  button:hover {
    background-color: #506c64;
    border-color: #506c64;
  }

  p {
    margin: auto 32px;
    font-size: large;
  }

  @media (min-width: 640px) {
    board {
      overflow-x: scroll;
    }
  }
</style>
