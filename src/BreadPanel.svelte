<script>
  import { getContext } from "svelte";

  // is array
  const cart = getContext("cart");

  const updateCart = (item) => {
    const existingItem = cart.find((i) => i.item === item);
    if (existingItem) {
      existingItem.quantity++;
    } else {
      cart.push({ item: item, quantity: 1 });
    }
    console.log(cart);
    resetSelection();
  };

  function resetSelection() {
    selectedBread = null;
  }

  let selectedBread;

  let breads = [
    {
      name: "Sourdough",
      price: 9,
    },
    {
      name: "Whole Wheat",
      price: 9,
    },
    {
      name: "White",
      price: 9,
    },
    {
      name: "Rye",
      price: 9,
    },
  ];

  function splitOptionsInHalf(options) {
    const half = Math.ceil(options.length / 2);
    return [options.slice(0, half), options.slice(half)];
  }

  const [breadsLeft, breadsRight] = splitOptionsInHalf(breads);
</script>

<div class="panel panel-opacity" style="margin-top: 1.5em;">
  <div class="level level-heading">
    <div class="level-item">
      <h2 class="title is-2">Breads</h2>
    </div>
  </div>
  <div class="panel-block">
    {#each breadsLeft as bread}
      <div class="control">
        <div class="radio">
          <label class="radio">
            <input
              type="radio"
              name="bread"
              value={bread.name}
              bind:group={selectedBread}
            />

            <strong>{bread.name}</strong>
          </label>
        </div>
      </div>
    {/each}
  </div>
  <div class="panel-block">
    {#each breadsRight as bread}
      <div class="control">
        <div class="radio">
          <label class="radio">
            <input
              type="radio"
              name="bread"
              value={bread.name}
              bind:group={selectedBread}
            />

            <strong>{bread.name}</strong>
          </label>
        </div>
      </div>
    {/each}
  </div>
  <div class="panel-block">
    <button
      class="button is-link is-fullwidth"
      style="background-color: rgb(239 186 171)"
      on:click={() => updateCart(selectedBread)}
      disabled={!selectedBread}
    >
      Add to Cart
    </button>
  </div>
</div>

<style>
  .panel-opacity {
    background-color: rgba(255, 255, 255, 0.7);
  }
  .level-heading {
    padding: 0.5em;
    background-color: rgb(0, 208, 200);
  }
</style>
