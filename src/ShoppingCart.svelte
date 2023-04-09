<script>
  export let cart = [];
</script>

<div class="shopping-cart">
  <h2 class="title is-2">Shopping Cart</h2>
  {#if $cart.size === 0}
    <p class="title is-3">Your cart is empty.</p>
  {:else}
    <ul>
      {#each $cart as item (item.id)}
        <li>
          <strong>{item.name}</strong> - Quantity: {item.quantity} - Price: ${item.price *
            item.quantity}
        </li>
      {/each}
    </ul>
    <p>
      Total: ${Array.from($cart.values()).reduce(
        (sum, item) => sum + item.price * item.quantity,
        0
      )}
    </p>
  {/if}
</div>

<style>
  /* .shopping-cart { */
  /* Add any desired styles for the shopping cart container */
  /* } */
</style>
