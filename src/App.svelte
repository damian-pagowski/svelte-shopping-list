<script>
  import Navbar from "./Navbar.svelte";
  import Item from "./Item.svelte";
  import AddItem from "./AddItem.svelte";

  let items = [
    { name: "Potatos", quantity: 100, completed: true },
    { name: "Tomatos", quantity: 101, completed: true }
  ];

  const addItem = e => {
    const newItem = e.detail;
    console.log("Adding: " + newItem);
    items = [...items, newItem];
  };

  const removeItem = e => {
    const removedItemName = e.detail;
    console.log("Removing: " + removedItemName);
    items = items.filter(i => i.name != removedItemName);
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
        <Item
          name={item.name}
          quantity={item.quantity}
          completed={item.completed}
          on:removeitem={removeItem} />
      {/each}
    {/if}
  </div>
</main>
