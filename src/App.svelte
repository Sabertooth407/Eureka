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
  import CustomCursor from './CustomCursor.svelte';
  import OurTeam from './OurTeam.svelte';
  import Schedule from './Schedule.svelte';

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
    '/oblivion': Oblivion,
    '/ourteam': OurTeam,
    '/schedule': Schedule
  };

  import { onMount, onDestroy } from "svelte";

  // --- Global state for zero gravity ---
  let zeroGravityActive = false;

  // Konami Code sequence
  const konamiSequence = [
    "ArrowUp", "ArrowUp",
    "ArrowDown", "ArrowDown",
    "ArrowLeft", "ArrowRight",
    "ArrowLeft", "ArrowRight",
    "b", "a"
  ];
  let keys = [];

  function handleKeyDown(e) {
    keys.push(e.key);
    if (keys.length > konamiSequence.length) keys.shift();

    if (JSON.stringify(keys) === JSON.stringify(konamiSequence)) {
      zeroGravityActive = !zeroGravityActive; // toggle mode
      if (zeroGravityActive) {
        activateZeroGravity();
      } else {
        deactivateZeroGravity();
      }
    }
  }

  function activateZeroGravity() {
    document.body.classList.add("zero-gravity");
    applyFloatToAll();
  }

  function deactivateZeroGravity() {
    document.body.classList.remove("zero-gravity");
    document.querySelectorAll("body *").forEach(el => {
      el.style.transform = "";
      el.style.transition = "";
    });
  }

  function applyFloatToAll() {
    document.querySelectorAll("body *").forEach(el => {
      el.style.transition = "transform 2s ease-in-out";
      el.style.display = "inline-block";
      animateFloat(el);
    });
  }

  function animateFloat(el) {
    function float() {
      if (!zeroGravityActive) return;
      const x = (Math.random() - 0.5) * 40;
      const y = (Math.random() - 0.5) * 40;
      const rotate = (Math.random() - 0.5) * 30;
      el.style.transform = `translate(${x}px, ${y}px) rotate(${rotate}deg)`;
      setTimeout(float, 2000);
    }
    float();
  }

  // Watch for new elements after route changes
  function observeDomChanges() {
    const observer = new MutationObserver(() => {
      if (zeroGravityActive) applyFloatToAll();
    });
    observer.observe(document.body, { childList: true, subtree: true });
  }

  onMount(() => {
    window.addEventListener("keydown", handleKeyDown);
    observeDomChanges();
  });

  onDestroy(() => {
    window.removeEventListener("keydown", handleKeyDown);
  });
</script>

<style>
  :global(body) {
    margin: 0;
    background-color: black;
    color: white;
    cursor: none !important;
  }
  :global(.zero-gravity) {
    overflow: hidden;
    position: relative;
  }
</style>

<CustomCursor size={15} intensity={1.1} />
<Background />
<Navbar />
<Router {routes} />
