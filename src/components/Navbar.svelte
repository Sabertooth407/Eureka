<script>
  import { link } from 'svelte-spa-router';
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
</style>

<nav>
  <a use:link href="/">Home</a>
  <a use:link href="/about">About</a>
  <a use:link href="/events">Events</a>
  <a use:link href="/contact">Contact</a>
</nav>
