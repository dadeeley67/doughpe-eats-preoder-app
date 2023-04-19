<script>
  import BreadPanel from "./BreadPanel.svelte";

  let breads = [
    {
      name: "sourdough",
      price: 9,
    },
    {
      name: "whole wheat",
      price: 9,
    },
    {
      name: "white",
      price: 9,
    },
    {
      name: "rye",
      price: 9,
    },
  ];
</script>

<div class="box panel-opacity" style="margin-top: 1.5em;">
  <div class="level level-heading">
    <div class="level-item">
      <h2 class="title is-2">Loaves</h2>
    </div>
  </div>

  {#each breads as bread}
    <BreadPanel {bread} />
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
