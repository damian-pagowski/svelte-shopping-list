<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  export let name;
  export let quantity;
  export let completed;
  
  let showControls = false;

  const toggleShowControls = () => {
    showControls = !showControls;
  };

  const toggleCompleted = () => {
    completed = !completed;
  };

  const deleteitem = () => {
    dispatch("removeitem", name);
  };
</script>

<style>
  .completed {
    text-decoration: line-through;
  }
</style>

<div class="card mt-3" style="width: 18rem;">
  <div class="card-body">

    <h5 class="card-title {completed ? 'completed' : ''}">Name: {name}</h5>
    <p class="card-text">Quantity: {quantity}</p>
    <div class="form-group form-check">

      <button class="btn btn-light" on:click={toggleShowControls}>
        <i class="fas fa-edit" />
      </button>
      <button class="btn btn-light" on:click={deleteitem}>
        <i class="fas fa-trash" />
      </button>
      <button class="btn btn-light" on:click={toggleCompleted}>
        <i class="far fa-check-square" />
      </button>
    </div>
    {#if showControls}
      <input class="mt-3" type="text" bind:value={name} />
      <input class="mt-3" type="number" bind:value={quantity} />
    {/if}
  </div>
</div>
