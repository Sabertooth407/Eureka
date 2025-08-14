<script>
  import Router from 'svelte-spa-router';
  import Navbar from './Navbar.svelte';
  import Home from './Home.svelte';
  import Background from './Background.svelte';
  import About from './About.svelte';
  import Events from './Events.svelte';
  import Registration from './Registration.svelte';
  import Contacts from './Contacts.svelte';
  import MazeFrenzy from './MazeFrenzy.svelte';
  const routes = {
    '/': Home,
    '/about': About,
    '/events': Events,
    '/registration': Registration,
    '/contact': Contacts,
    '/mazefrenzy': MazeFrenzy
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
