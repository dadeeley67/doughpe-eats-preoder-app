<script>
  import { getContext } from "svelte";
  const cart = getContext("cart");
  let name = "";
  let emailOrPhone = "";

  function handleSubmit() {
    // Process the form data and send it to the backend
    console.log(name, emailOrPhone, cart);
  }
</script>

<!-- {#if cart.length > 0} -->
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

<!-- {/if} -->
<style>
  .panel-opacity {
    background-color: rgba(255, 255, 255, 0.7);
    padding: 4em;
  }
  .is-primary {
    border-color: rgb(0, 208, 200) !important;
  }
  .is-danger {
    border-color: rgb(239, 186, 171) !important;
  }
</style>
