<script>
  import { writable } from "svelte/store";
  import ShoppingCart from "./ShoppingCart.svelte";
  import NavBar from "./NavBar.svelte";
  import BagelPanel from "./BagelPanel.svelte";
  import BreadPanel from "./BreadPanel.svelte";

  const cart = writable(new Map());

  let bakedGoods = [
    {
      id: 1,
      category: "Bagels",
      options: [
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
      ],
      spread: [
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
      ],
    },
    {
      id: 2,
      category: "Bread",
      options: [
        {
          name: "Sourdough",
          price: 9,
        },
        {
          name: "Glass Bread",
          price: 6,
        },
        {
          name: "Rye",
          price: 9,
        },
        {
          name: "80/20 White and Whole Wheat",
          price: 9,
        },
      ],
    },
  ];

  let selectedItems = new Map();
  let name = "";
  let emailOrPhone = "";

  function handleQuantityChange(event, item) {
    const quantity = parseInt(event.target.value);
    cart.update((currentCart) => {
      if (quantity > 0) {
        currentCart.set(item.id, { ...item, quantity });
      } else {
        currentCart.delete(item.id);
      }
      return new Map(currentCart); // return a new Map instance to trigger reactivity
    });
  }

  function splitOptionsInHalf(options) {
    const half = Math.ceil(options.length / 2);
    return [options.slice(0, half), options.slice(half)];
  }

  let bagelOptions = splitOptionsInHalf(bakedGoods[0].options);
  let bagels1 = bagelOptions[0];
  let bagels2 = bagelOptions[1];
  let spreadOptions = splitOptionsInHalf(bakedGoods[0].spread);
  let breadOptions = splitOptionsInHalf(bakedGoods[1].options);

  function handleSubmit() {
    // Process the form data and send it to the backend
    console.log(selectedItems, name, emailOrPhone);
  }
</script>

<!-- NavBar -->
<NavBar />

<div class="panel">
  <!-- Add the ShoppingCart component below the form -->
  <ShoppingCart {cart} />

  <BagelPanel />
  <BreadPanel />

  <div class="container">
    <form on:submit|preventDefault={handleSubmit}>
      <div>
        <label for="name">Name:</label>
        <input
          class="input is-danger"
          type="text"
          id="name"
          bind:value={name}
          required
        />
      </div>

      <div>
        <label for="emailOrPhone">Email or Phone:</label>
        <input
          class="input is-primary"
          type="text"
          id="emailOrPhone"
          bind:value={emailOrPhone}
          required
        />
      </div>

      <button class="button" type="submit">Proceed to Payment</button>
    </form>
  </div>
</div>

<style>
  .panel {
    padding-top: 10em;
    padding-left: 4em;
    padding-right: 4em;
    padding-bottom: 10em;
  }
</style>
