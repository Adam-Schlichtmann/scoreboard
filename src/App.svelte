<script lang="ts">
  import Column from "./Column.svelte";
  import Labels from "./Labels.svelte";

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
</script>

<round>
  <button on:click={decrement}>Previous</button>
  <p>ROUND: {round + 1}</p>
  <button on:click={increment}>Next</button>
</round>
<board>
  <Labels />
  {#each game as player}
    <Column player={player.name} score={player.score[round]} />
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
  }

  board {
    display: flex;
    justify-content: center;
    flex-direction: row;
  }

  button {
    background-color: #75b8c8;
    border-color: #75b8c8;
    border-radius: 1em;
  }
  button:active {
    background-color: #506c64;
    border-color: #506c64;
  }
  p {
    margin: auto 32px;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
