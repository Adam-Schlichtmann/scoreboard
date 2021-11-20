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
  <p>Names</p>
  <p>{Feathers.label}</p>
  <p>{BonusCards.label}</p>
  <p>{EndOfRound.label}</p>
  <p>{Eggs.label}</p>
  <p>{TuckedCards.label}</p>
  <p>{CachedFood.label}</p>
</div>
