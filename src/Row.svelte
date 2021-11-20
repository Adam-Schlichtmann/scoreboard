<script lang="ts">
  type Input = { value: number; label: string };

  let Feathers: Input = { value: 0, label: "Feathers" };
  let BonusCards: Input = { value: 0, label: "Bonus" };
  let EndOfRound: Input = { value: 0, label: "End of Round Goal" };
  let Eggs: Input = { value: 0, label: "Eggs" };
  let TuckedCards: Input = { value: 0, label: "Tucked Cards" };
  let CachedFood: Input = { value: 0, label: "Cached Food" };
</script>

<div>
  <input type="number" bind:value={Feathers.value} min="0" max="10" />
  <input type="number" bind:value={BonusCards.value} min="0" max="10" />
  <input type="number" bind:value={EndOfRound.value} min="0" max="10" />
  <input type="number" bind:value={Eggs.value} min="0" max="10" />
  <input type="number" bind:value={TuckedCards.value} min="0" max="10" />
  <input type="number" bind:value={CachedFood.value} min="0" max="10" />
</div>
