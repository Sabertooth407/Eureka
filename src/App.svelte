<script>
  import Router from 'svelte-spa-router';
  import Navbar from './components/Navbar.svelte';
  import Home from './pages/Home.svelte';
  import Background from './components/Background.svelte';

  const routes = {
    '/': Home,
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
