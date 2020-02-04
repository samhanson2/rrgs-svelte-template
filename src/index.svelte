<script>
  let name = `Mr. Hullen`;
  let temp = 20;
</script>

<style>
    button {
        display: block;
        margin-top: 1em;
    }
</style>

<div class="section">
  <h1 class="title">Chocolate Drink Order</h1>

  <label class="label">
    Name:
    <input class="input" type="text" bind:value={name} />
  </label>

  <label class="label">
    Drink temperature:
    <input class="input" type="range" min="0" max="100" bind:value={temp} />
  </label>
  {temp}°C ({Math.round(temp * 1.8) + 32}°F)

  {#if temp < 40}
    ... fairly tepid ❄
  {:else if temp > 90}
    ... very hot!!! 🔥
  {:else}
    ... looks good ☕
  {/if}

  <button class="button is-success">Submit</button>
</div>
