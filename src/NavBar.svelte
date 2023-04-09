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

<nav
  class="navabar"
  style="height: {scrolled
    ? '50px'
    : '100px'}; background-color: rgba(0, 0, 0, {scrolled ? 0.7 : 0.9});"
  aria-label="main navigation"
>
  <div class="navbar-brand level-item">
    <a class="navbar-item" href="https://bulma.io">
      <img
        src="./images/logo.png"
        type="image/png"
        width={scrolled ? 175 : 300}
        alt="Doughpe Eats"
        style="transition: all 0.5s;"
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
