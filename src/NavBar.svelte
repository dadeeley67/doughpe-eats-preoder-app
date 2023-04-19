<script>
  import { onMount } from "svelte";

  let scrolled = false;

  function updateNavbar() {
    const yOffset = window.pageYOffset;
    scrolled = yOffset > 50;
  }

  onMount(() => {
    window.addEventListener("scroll", updateNavbar);
    return () => {
      window.removeEventListener("scroll", updateNavbar);
    };
  });
</script>

<nav class="navabar" aria-label="main navigation">
  <div class="navbar-brand level-item">
    <a class="navbar-item" href="/">
      <img
        src="./images/logo.png"
        type="image/png"
        width="250px"
        alt="Doughpe Eats"
      /></a
    >
  </div>
</nav>

<style>
  .navbar-item img {
    max-height: none;
  }
  .navabar {
    width: 100%;
    position: fixed;
    top: 0;
    left: 0;
    background-color: rgba(0, 0, 0, 0.9);
    /* height: 300px; */
    display: flex;
    align-items: center;
    justify-content: space-around;
    transition: all 0.5s;
    z-index: 100;
  }
</style>
