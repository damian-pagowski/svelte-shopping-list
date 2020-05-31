<script>
  import Navbar from "./Navbar.svelte";
  import Item from "./Item.svelte";
  import AddItem from "./AddItem.svelte";

  let items = [
    { name: "Potatos", quantity: 100 },
    { name: "Tomatos", quantity: 101 }
  ];

  const addItem = e => {
    const newItem = e.detail;
    console.log(newItem);
    items = [...items, newItem];
  };
</script>

<style>
  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>

<main>
  <Navbar />
  <div class="container">
    <AddItem on:additem={addItem} />
    <hr class="my-4" />

    {#if items.length == 0}
      <p>Shopping List Empty</p>
    {:else}
      {#each items as item}
        <Item name={item.name} quantity={item.quantity} />
      {/each}
    {/if}
  </div>
</main>
