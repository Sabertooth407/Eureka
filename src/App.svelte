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
  import ThePhysicistsCode from './ThePhysicistsCode.svelte';
  import PhyMUN from './PhyMUN.svelte';
  import AdAstra from './AdAstra.svelte';
  import NewtonsMemeathon from './NewtonsMemeathon.svelte';
  import TriPhysicsTournament from './TriPhysicsTournament.svelte';
  import Oblivion from './Oblivion.svelte';
  const routes = {
    '/': Home,
    '/about': About,
    '/events': Events,
    '/registration': Registration,
    '/contact': Contacts,
    '/mazefrenzy': MazeFrenzy,
    '/thephysicistscode': ThePhysicistsCode,
    '/phymun': PhyMUN,
    '/adastra': AdAstra,
    '/newtonsmemeathon': NewtonsMemeathon,
    '/triphysicstournament': TriPhysicsTournament,
    '/oblivion': Oblivion
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
