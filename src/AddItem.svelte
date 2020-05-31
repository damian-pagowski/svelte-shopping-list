<script>
  let item = {
    name: "",
    quantity: 0
  };

  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  const onSubmit = e => {
    e.preventDefault();
    console.log("onSubmit called")
    dispatch("additem", item);
    item = {
      name: "",
      quantity: 0
    };
  };
</script>

<form class="mt-3" on:submit={onSubmit}>
  <div class="form-group">
    <label for="name">Name</label>
    <input
      type="text"
      name="name"
      class="form-control"
      id="name"
      bind:value={item.name} />
  </div>
  <div class="form-group">
    <label for="points">Quantity</label>
    <input
      type="number"
      class="form-control"
      id="points"
      bind:value={item.quantity} />
  </div>

  <button type="submit" class="btn btn-primary">Submit</button>
</form>
