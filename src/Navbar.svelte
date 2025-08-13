<script>
  import { link, location } from 'svelte-spa-router';
  let menuOpen = false;

  function toggleMenu() {
    menuOpen = !menuOpen;
  }

  function isMobile() {
    return typeof window !== 'undefined' && window.innerWidth <= 768;
  }
</script>

<style>
  nav {
    position: relative; /* no fixed positioning */
    height: 60px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'FuturaBold', sans-serif;
    width: 100%;
    max-width: 1000px;
    margin: 0 auto; /* center horizontally */
  }

  .links {
    display: flex;
    gap: 3rem;
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

  .burger {
    display: none;
    flex-direction: column;
    justify-content: center;
    gap: 5px;
    cursor: pointer;
    width: 30px;
    height: 25px;
    z-index: 2000;
    position: absolute;
    right: 1rem;
    top: 1rem;
  }

  .burger div {
    height: 3px;
    width: 25px;
    background: white;
    border-radius: 2px;
    transition: 0.3s;
  }

  .burger.open div:nth-child(1) {
    transform: rotate(45deg) translate(5px, 5px);
  }
  .burger.open div:nth-child(2) {
    opacity: 0;
  }
  .burger.open div:nth-child(3) {
    transform: rotate(-45deg) translate(6px, -6px);
  }

  @media (max-width: 768px) {
    nav {
      justify-content: flex-end;
      padding: 0 1rem;
    }
    .links {
      display: none;
    }
    .links.open {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      gap: 2rem;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.9);
      z-index: 1050;
    }
    .burger {
      display: flex;
    }
  }
</style>

<!-- Only render if NOT (mobile + home page) -->
{#if !(isMobile() && $location === '/')}

  <nav>
    <div class="burger {menuOpen ? 'open' : ''}" on:click={toggleMenu}>
      <div></div>
      <div></div>
      <div></div>
    </div>

    <div class="links {menuOpen ? 'open' : ''}">
      <a use:link href="/" on:click={() => menuOpen = false}>Home</a>
      <a use:link href="/registration" on:click={() => menuOpen = false}>Register</a>
      <a use:link href="/about" on:click={() => menuOpen = false}>About</a>
      <a use:link href="/events" on:click={() => menuOpen = false}>Events</a>
      <a use:link href="/contact" on:click={() => menuOpen = false}>Contact</a>
    </div>
  </nav>

{/if}
