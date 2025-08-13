<script>
  import Router from 'svelte-spa-router';
  import Navbar from './Navbar.svelte';
  import Home from './Home.svelte';
  import Background from './Background.svelte';
  import About from './About.svelte';
  import Events from './Events.svelte';
  const routes = {
    '/': Home,
    '/about': About,
    '/events': Events
  };
</script>


<style>
  :global(body) {
    margin: 0;
    font-family: system-ui, sans-serif;
    background-color: black;
    color: white;
  }
</style>
<Background />
<Navbar />
<Router {routes} />
