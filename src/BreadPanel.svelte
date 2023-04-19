<script>
  import { getContext } from "svelte";

  export let bread;

  // is array
  const cart = getContext("cart");

  const updateCart = (quantity) => {
    const existingItem = cart.find((i) => i.item === bread.name);
    if (existingItem) {
      existingItem.quantity += quantity;
    } else {
      cart.push({ item: bread.name, quantity: quantity });
    }
    console.log(cart);
    resetSelection();
  };

  let showQuantityInput = false;
  let quantity = 1;

  function toggleQuantityInput() {
    showQuantityInput = !showQuantityInput;
  }

  function resetSelection() {
    toggleQuantityInput();
    quantity = 1;
  }
</script>

<div style="margin-bottom: 1em;">
  <div class="level">
    <div class="level-left">
      <div class="level-item">
        <h3 class="title is-3">
          {bread.name}
        </h3>
      </div>
    </div>
    <div class="level-right">
      <div class="level-item">
        {#if !showQuantityInput}
          <button
            class="button is-link is-fullwidth"
            style="background-color: rgb(239 186 171)"
            on:click={() => toggleQuantityInput()}
          >
            Add to Cart
          </button>
        {:else}
          <div class="field has-addons">
            <div class="control">
              <input
                type="number"
                class="input"
                min="1"
                bind:value={quantity}
                on:keypress={() => updateCart(quantity)}
              />
            </div>
            <div class="control">
              <button
                class="button is-link"
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
</div>

<!-- <div class="panel-block">
  <div class="control">
    <div class="radio">
      <label class="radio">
        <input
          type="radio"
          name="bread"
          value={bread.name}
          bind:group={selectedBread}
        />

        <p class="title is-3">{bread.name}</p>
      </label>
    </div>
  </div>
</div> -->
