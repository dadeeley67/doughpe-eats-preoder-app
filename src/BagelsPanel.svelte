<script>
  import BagelPanel from "./BagelPanel.svelte";

  let bagels = [
    {
      name: "plain",
      price: 2.5,
    },
    {
      name: "spicy everything",
      price: 2.5,
    },
    {
      name: "black & white sesame",
      price: 2.5,
    },
    {
      name: "poppy seed",
      price: 2.5,
    },
  ];
</script>

<div class="box panel-opacity" style="margin-top: 1.5em;">
  <div class="level level-heading">
    <div class="level-item">
      <h2 class="title is-2">Bagels</h2>
    </div>
  </div>

  {#each bagels as bagel}
    <BagelPanel {bagel} />
  {/each}
</div>

<style>
  .panel-opacity {
    background-color: rgba(255, 255, 255, 0.7);
  }
  .level-heading {
    padding: 0.5em;
    background-color: rgb(0, 208, 200);
    border-radius: 4px;
  }
</style>
