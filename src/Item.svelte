<script>
  export let name;
  export let quantity;
  const decreaseQuantity = () => {
    quantity -= 1;
  };
  const increaseQuantity = () => {
    quantity += 1;
  };

  const deleteitem = () => {
    console.log("deleted");
  };

  const toggleShowControls = () => {
    showControls = !showControls;
  };
  let showControls = false;
</script>

<div class="card mt-3" style="width: 18rem;">
  <div class="card-body">

    <h5 class="card-title">Name: {name}</h5>
    <p class="card-text">Quantity: {quantity}</p>
    <div class="form-group form-check">
      <!-- <input
        type="checkbox"
        class="form-check-input"
        id="showControls"
        bind:checked={showControls} /> -->
      <!-- <label class="form-check-label" for="showControls">Show Controls</label> -->
      <button class="btn btn-light" on:click={toggleShowControls}>
        <i class="fas fa-edit" />
      </button>
      <button class="btn btn-light" on:click={deleteitem}>
        <i class="fas fa-trash" />
      </button>
    </div>
    {#if showControls}
      <button class="btn btn-primary" on:click={increaseQuantity}>+1</button>
      <button class="btn btn-primary" on:click={decreaseQuantity}>-1</button>
      <input class="mt-3" type="number" bind:value={quantity} />
    {/if}
  </div>
</div>
