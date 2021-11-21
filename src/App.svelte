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
  <input value="Names" disabled />
  <input value="Feathers" disabled />
  <input value="Bonus" disabled />
  <input value="End of Round Goal" disabled />
  <input value="Eggs" disabled />
  <input value="Tucked Cards" disabled />
  <input value="Cached Food" disabled />
  <input value="Total" disabled />
  {#each game as player, i}
    <input bind:value={player.name} placeholder="enter your name" />
    <input
      bind:value={player.score[round].feathers}
      type="number"
      min="0"
      max="200"
    />
    <input
      bind:value={player.score[round].bonus}
      type="number"
      min="0"
      max="200"
    />
    <input
      bind:value={player.score[round].endOfRound}
      type="number"
      min="0"
      max="200"
    />
    <input
      bind:value={player.score[round].eggs}
      type="number"
      min="0"
      max="200"
    />
    <input
      bind:value={player.score[round].tucked}
      type="number"
      min="0"
      max="200"
    />
    <input
      bind:value={player.score[round].cached}
      type="number"
      min="0"
      max="200"
    />
    <input disabled bind:value={totals[i]} type="number" min="0" max="200" />
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
    grid-template-columns: 2fr repeat(5 1fr);
    grid-template-rows: repeat(8, 1fr);
    grid-column-gap: 10px;
    grid-auto-flow: column;
  }

  input {
    border-color: #220c10;
    background-color: #75b8c8;
    color: #220c10;
    outline: none;
    margin: 2px;
  }
  button {
    background-color: #75b8c8;
    border-color: #75b8c8;
    border-radius: 1em;
    min-width: 100px;
    width: 10%;
  }

  button:active,
  button:hover {
    background-color: #506c64;
    border-color: #506c64;
  }

  p {
    margin: auto 32px;
  }

  @media (min-width: 640px) {
    board {
      overflow-x: scroll;
    }
  }
</style>
