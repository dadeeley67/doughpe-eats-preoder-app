<script>
  import { getContext } from "svelte";
  const cart = getContext("cart");

  let bagels = [
    {
      name: "Plain",
      price: 2.5,
    },
    {
      name: "Spicy Everything",
      price: 2.5,
    },
    {
      name: "Black & White Sesame",
      price: 2.5,
    },
    {
      name: "Poppy Seed",
      price: 2.5,
    },
  ];

  let spreads = [
    {
      name: "Plain Cream Cheese",
      price: 1.5,
    },
    {
      name: "Chive Cream Cheese",
      price: 1.5,
    },
    {
      name: "Butter",
      price: 0.5,
    },
    {
      name: "Vegan Cream Cheese",
      price: 1.5,
    },
    {
      name: "Vegan Butter",
      price: 0.5,
    },
  ];

  function splitOptionsInHalf(options) {
    const half = Math.ceil(options.length / 2);
    return [options.slice(0, half), options.slice(half)];
  }

  let selectedBagel;

  let selectedSpread;

  const resetSelection = () => {
    selectedBagel = null;
    selectedSpread = null;
  };

  const updateCart = (item) => {
    const existingItem = cart.find(
      (i) => i.item === item && i.options === selectedSpread
    );
    if (existingItem) {
      existingItem.quantity++;
    } else {
      cart.push({ item: item, options: selectedSpread, quantity: 1 });
    }
    console.log(cart);
    resetSelection();
  };

  const [bagelsLeft, bagelsRight] = splitOptionsInHalf(bagels);
  const [spreadsLeft, spreadsRight] = splitOptionsInHalf(spreads);
</script>

<div class="panel panel-opacity" style="margin-top: 1.5em;">
  <div class="level level-heading">
    <div class="level-item">
      <h2 class="title is-2">Bagels</h2>
    </div>
  </div>

  <div class="panel-block">
    {#each bagelsLeft as bagel}
      <div class="control">
        <div class="radio is-fullwidth">
          <label class="radio">
            <input
              type="radio"
              name="bagel"
              value={bagel.name}
              bind:group={selectedBagel}
              required
            />
            <strong>{bagel.name}</strong>
          </label>
        </div>
      </div>
    {/each}
  </div>
  <div class="panel-block">
    {#each bagelsRight as bagel}
      <div class="control">
        <div class="radio is-fullwidth">
          <label class="radio">
            <input
              type="radio"
              name="bagel"
              value={bagel.name}
              bind:group={selectedBagel}
              required
            />
            <strong>{bagel.name}</strong>
          </label>
        </div>
      </div>
    {/each}
  </div>
  <div class="panel-block">
    {#each spreadsLeft as spread}<div class="control">
        <div class="radio is-fullwidth">
          <label class="radio">
            <input
              type="radio"
              name="spread"
              value={spread.name}
              bind:group={selectedSpread}
            />
            <strong>{spread.name}</strong>
          </label>
        </div>
      </div>
    {/each}
  </div>
  <div class="panel-block">
    {#each spreadsRight as spread}<div class="control">
        <div class="radio is-fullwidth">
          <label class="radio">
            <input
              type="radio"
              name="spread"
              value={spread.name}
              bind:group={selectedSpread}
            />
            <strong>{spread.name}</strong>
          </label>
        </div>
      </div>
    {/each}
  </div>
  <div class="panel-block">
    <button
      class="button is-link is-fullwidth"
      style="background-color: rgb(239 186 171);"
      on:click={() => updateCart(selectedBagel)}
      disabled={!selectedBagel}>Add to Cart</button
    >
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
