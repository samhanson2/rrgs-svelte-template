<script>
  let box = {
    locked: true,
    unlock: () => { box.locked = false },
    lock: () => { box.locked = true },
    contents: [
        "Thing 1",
        "Thing 2"
    ]
  }
</script>

<style>
    .content {
        width: 50%;
        margin: 0 auto;
    }
</style>

<div class="content">
  <div class="section">
    {#if box.locked}
      <p>The box is <span class="is-size-4 is-uppercase has-text-weight-bold has-text-success">locked</span></p>
      <button class="button is-danger" on:click={box.unlock}>Unlock</button>
    {:else}
      <p>The box is <span class="is-size-4 is-uppercase has-text-weight-bold has-text-danger">unlocked</span></p>
      <button class="button is-success" on:click={box.lock}>Lock</button>
    {/if}
  </div>

  <div class="box">
    <p class="title is-5">Contents:</p>
    {#if box.locked}
      <p>Can't open!</p>
    {:else}
      <ul class="list">
        {#each box.contents as item}
          <li class="list-item">{item}</li>
        {/each}
      </ul>
    {/if}
  </div>
</div>
