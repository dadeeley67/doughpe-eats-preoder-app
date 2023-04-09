<script>
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

  const [bagelsLeft, bagelsRight] = splitOptionsInHalf(bagels);
  const [spreadsLeft, spreadsRight] = splitOptionsInHalf(spreads);
</script>

<div class="panel" style="margin-top: 1.5em;">
  <p class="panel-heading" style="background-color: rgba(255, 255, 255, 0.7);">
    Bagel
  </p>
  <div class="panel-block">
    {#each bagelsLeft as bagel}
      <div class="control">
        <div class="radio is-fullwidth">
          <label class="radio">
            <input type="radio" name="bagel" value={bagel.name} required />
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
            <input type="radio" name="bagel" value={bagel.name} required />
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
            <input type="radio" name="spread" value={spread.name} />
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
            <input type="radio" name="spread" value={spread.name} />
            <strong>{spread.name}</strong>
          </label>
        </div>
      </div>
    {/each}
  </div>
  <div class="panel-block">
    <button
      class="button is-link is-fullwidth"
      style="background-color: rgb(239 186 171);">Add to Cart</button
    >
  </div>
</div>
