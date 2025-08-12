<script>
  import { link } from 'svelte-spa-router';

  let menuOpen = false;

  function toggleMenu() {
    menuOpen = !menuOpen;
  }
</script>

<style>
  nav {
    position: fixed;
    top: 0;
    left: 50%;
    transform: translateX(-50%);
    height: 60px;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 3rem;
    z-index: 1000;
    background: none;
    font-family: 'FuturaBold', sans-serif;
    padding-bottom: 1.5rem;
  }

  a {
    color: white;
    text-decoration: none;
    font-size: 1.2rem;
    position: relative;
    transition: color 0.3s ease;
  }

  a::after {
    content: '';
    position: absolute;
    left: 0;
    bottom: -4px;
    width: 0;
    height: 2px;
    background: linear-gradient(90deg, orange, white);
    transition: width 0.3s ease;
  }

  a:hover {
    color: orange;
  }

  a:hover::after {
    width: 100%;
  }

  /* Burger button */
  .burger {
    display: none;
    flex-direction: column;
    justify-content: center;
    gap: 5px;
    cursor: pointer;
    width: 30px;
    height: 25px;
  }

  .burger div {
    height: 3px;
    background: white;
    border-radius: 2px;
    transition: 0.3s;
  }

  /* Mobile styles */
  @media (max-width: 768px) {
    nav {
      justify-content: space-between;
      padding: 0 1rem;
      transform: none;
      left: 0;
    }

    .links {
      position: absolute;
      top: 60px;
      left: 0;
      width: 100%;
      background: rgba(0, 0, 0, 0.9);
      flex-direction: column;
      align-items: center;
      gap: 1.5rem;
      padding: 1rem 0;
      display: none;
    }

    .links.open {
      display: flex;
    }

    .burger {
      display: flex;
    }
  }
</style>

<nav>
  <div class="burger" on:click={toggleMenu}>
    <div></div>
    <div></div>
    <div></div>
  </div>

  <div class="links {menuOpen ? 'open' : ''}">
    <a use:link href="/">Home</a>
    <a use:link href="/about">About</a>
    <a use:link href="/events">Events</a>
    <a use:link href="/contact">Contact</a>
  </div>
</nav>
