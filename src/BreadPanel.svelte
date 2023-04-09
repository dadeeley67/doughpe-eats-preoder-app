<script>
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

<div class="panel" style="margin-top: 1.5em;">
  <p class="panel-heading" style="background-color: rgba(255, 255, 255, 0.7);">
    Bread
  </p>
  <div class="panel-block">
    {#each breadsLeft as bread}
      <div class="control">
        <div class="radio">
          <label class="radio">
            <input type="radio" name="bread" value={bread.name} />
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
            <input type="radio" name="bread" value={bread.name} />
            <strong>{bread.name}</strong>
          </label>
        </div>
      </div>
    {/each}
  </div>
  <div class="panel-block">
    <button
      class="button is-link is-fullwidth"
      style="background-color: rgb(0 208 200)">Add to Cart</button
    >
  </div>
</div>
