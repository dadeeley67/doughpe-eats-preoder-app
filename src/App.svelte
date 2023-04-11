<script>
  import { setContext } from "svelte";
  import ShoppingCart from "./ShoppingCart.svelte";
  import NavBar from "./NavBar.svelte";
  import BagelPanel from "./BagelPanel.svelte";
  import BreadPanel from "./BreadPanel.svelte";

  let cart = new Array();
  setContext("cart", cart);

  let selectedItems = new Map();
  let name = "";
  let emailOrPhone = "";

  function handleSubmit() {
    // Process the form data and send it to the backend
    console.log(selectedItems, name, emailOrPhone);
  }
</script>

<div class="content">
  <!-- NavBar -->
  <NavBar />

  <div class="panel">
    <!-- Add the ShoppingCart component below the form -->
    <!-- <ShoppingCart {cart} /> -->

    <BagelPanel />
    <BreadPanel />

    <div>
      <div class="panel panel-opacity">
        <form on:submit|preventDefault={handleSubmit}>
          <div class="field">
            <label for="name"><strong>Name:</strong></label>
            <input
              class="input is-danger"
              type="text"
              id="name"
              bind:value={name}
              required
            />
            <label for="emailOrPhone"><strong>Email or Phone:</strong></label>
            <input
              class="input is-primary"
              type="text"
              id="emailOrPhone"
              bind:value={emailOrPhone}
              required
            />
          </div>

          <button
            class="button is-link"
            style="background-color: rgb(0, 208, 200);"
            type="submit">Proceed to Payment</button
          >
        </form>
      </div>
    </div>
  </div>
</div>

<style>
  .panel {
    box-shadow: none;
  }
  .content {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    overflow: auto;
    padding: 20px;
    padding-top: 6em;
    padding-left: 4em;
    padding-right: 4em;
    padding-bottom: 4em;
  }
  .panel-opacity {
    background-color: rgba(255, 255, 255, 0.7);
    padding: 4em;
  }
</style>
