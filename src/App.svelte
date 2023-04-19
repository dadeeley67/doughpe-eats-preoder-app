<script>
  import { setContext } from "svelte";
  // import ShoppingCart from "./ShoppingCart.svelte";
  import PreOrderNotice from "./PreOrderNotice.svelte";
  import NavBar from "./NavBar.svelte";
  import BagelsPanel from "./BagelsPanel.svelte";
  import BreadsPanel from "./BreadsPanel.svelte";
  import SubmitOrder from "./SubmitOrder.svelte";

  let cart = new Array();
  setContext("cart", cart);
</script>

<div class="content">
  <!-- NavBar -->
  <NavBar />

  <div class="panel">
    <!-- Add the ShoppingCart component below the form -->
    <!-- <ShoppingCart {cart} /> -->
    <PreOrderNotice />
    <BagelsPanel />
    <BreadsPanel />
    <SubmitOrder />
  </div>
</div>

<style>
  .panel {
    box-shadow: none;
    font-size: 1.2em;
  }
  .content {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    overflow: auto;
    padding: 20px;
    padding-top: 10em;
    padding-left: 4em;
    padding-right: 4em;
    padding-bottom: 4em;
  }
</style>
