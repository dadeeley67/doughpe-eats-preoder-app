<script>
  export let bagel;

  import { getContext } from "svelte";
  const cart = getContext("cart");
  let spreads = [
    {
      name: "none",
      price: 0,
    },
    {
      name: "plain cream cheese",
      price: 1.5,
    },
    {
      name: "chive cream cheese",
      price: 1.5,
    },
    {
      name: "butter",
      price: 0.5,
    },
    {
      name: "vegan cream cheese",
      price: 1.5,
    },
    {
      name: "vegan butter",
      price: 0.5,
    },
  ];
  let selectedSpread = "none";

  let spreadDisplayPanel = false;

  let quantity = 1;

  let showQuantityInput = false;

  const toggleQuantityInput = () => {
    toggleSpreadDisplay();
    showQuantityInput = !showQuantityInput;
  };

  const toggleSpreadDisplay = () => {
    spreadDisplayPanel = !spreadDisplayPanel;
  };

  const updateCart = (quantity) => {
    const existingItem = cart.find(
      (i) => i.item === bagel.name && i.options === selectedSpread
    );
    if (existingItem) {
      existingItem.quantity += quantity;
    } else {
      cart.push({
        item: bagel.name,
        options: selectedSpread,
        quantity: quantity,
      });
    }
    console.log(cart);
    resetSelection();
  };

  const resetSelection = () => {
    selectedSpread = "none";
    quantity = 1;

    toggleQuantityInput();
    if (spreadDisplayPanel) {
      toggleSpreadDisplay();
    }
  };
</script>

<div style="margin-bottom: 1em;">
  <div class="level">
    <div class="level-left">
      <div class="level-item">
        <h3 class="title is-3">{bagel.name}</h3>
      </div>
    </div>
    <div class="level-right">
      <div class="level-item">
        {#if !showQuantityInput}
          <!-- <div class="field has-addons">
            <div class="control"> -->
          <button
            class="button is-link is-fullwidth"
            style="background-color: rgb(239 186 171)"
            on:click={() => toggleQuantityInput()}
            on:keypress={() => toggleQuantityInput()}
          >
            Add to Cart
          </button>
          <!-- </div>
          </div> -->
        {:else}
          <div class="field has-addons">
            <div class="control">
              <input
                type="number"
                class="input is-primary"
                min="1"
                bind:value={quantity}
              />
            </div>
            <div class="control">
              <button
                class="button is-link is-fullwidth"
                style="background-color: rgb(239 186 171);"
                on:click={() => updateCart(quantity)}
                on:keypress={() => updateCart(quantity)}
              >
                Add to Cart
              </button>
            </div>
            <div class="control">
              <button
                class="button is-link is-fullwidth"
                style="background-color: rgb(0, 208, 200);"
                on:click={() => resetSelection()}
                on:keypress={() => resetSelection()}
              >
                Cancel
              </button>
            </div>
          </div>
        {/if}
      </div>
    </div>
  </div>
  {#if spreadDisplayPanel}
    <div class="control">
      {#each spreads as spread}
        <div class="radio">
          <label class="radio">
            <input
              type="radio"
              name="spread"
              value={spread.name}
              checked={spread.name === selectedSpread}
              required
              bind:group={selectedSpread}
              on:keypress={() => updateCart(quantity)}
            />
            <strong>{spread.name}</strong>
          </label>
        </div>
      {/each}
    </div>
  {/if}
</div>

<style>
  .is-primary {
    border-color: rgb(0, 208, 200) !important;
  }
</style>
