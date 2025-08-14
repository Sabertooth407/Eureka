<script>
  import { link } from 'svelte-spa-router';

  const events = [
    { name: "Maze Frenzy", img: "/mazefrenzy.png", link: "/mazefrenzy" },
    { name: "The Physicist's Code", img: "/physicistscode.png", link: "/thephysicistscode" },
    { name: "PhyMUN", img: "/phymun.png", link: "/phymun" },
    { name: "Ad Astra Abyssoque", img: "/adastra.png", link: "/adastra" },
    { name: "Newton's Meme-athon", img: "/newtonsmemeathon.png", link: "/newtonsmemeathon" },
    { name: "Tri Physics Tournament", img: "/triphysics.png", link: "/triphysicstournament" },
    { name: "Oblivion", img: "/oblivion.png", link: "/oblivion" }
  ];
</script>

<style>
  @font-face {
    font-family: 'Transcity DEMO';
    src: url('/Transcity DEMO.otf') format('opentype');
    font-weight: bold;
    font-style: normal;
  }
  .page-wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding-bottom: 24px;
  }
  

  h1 {
    font-family: 'Transcity DEMO', sans-serif;
    font-size: 3rem;
    color: white;
    margin-bottom: 0.5rem;
    letter-spacing: 2px;
    text-align: center;
  }

  .events-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 16px 20px;
    width: 100%;
    max-width: 1100px;
    padding: 0 16px;
    align-content: center;
  }

  .event-card {
    position: relative;
    flex: 0 0 210px;
    max-width: 210px;
    overflow: hidden;
    border-radius: 14px;
    cursor: pointer;
    transition: transform 260ms cubic-bezier(.2,.9,.2,1);
    text-decoration: none;
    color: white;
  }

  .event-card img {
    width: 100%;
    height: 210px;
    object-fit: contain;
    display: block;
    background: rgba(255,255,255,0.02);
  }

  .event-card:hover {
    transform: translateY(-6px) scale(1.03);
  }

  /* Overlay for desktop hover */
  .overlay {
    position: absolute;
    inset: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    background: rgba(0,0,0,0.7);
    color: #fff;
    font-weight: 700;
    font-family: 'FuturaBold', system-ui, sans-serif;
    font-size: 1rem;
    text-align: center;
    opacity: 0;
    transition: opacity 240ms ease;
  }

  .event-card:hover .overlay {
    opacity: 1;
  }

  /* Event name text below image for mobile */
  .event-name-mobile {
    display: none;
    font-family: 'FuturaBold', system-ui, sans-serif;
    text-align: center;
    font-size: 1rem;
    margin-top: 0.5rem;
  }

  @media (max-width: 768px) {
    .event-card {
      flex: 0 0 160px;
      max-width: 160px;
    }
    .event-card img {
      height: 160px;
    }
    .overlay {
      display: none; /* disable overlay on mobile */
    }
    .event-name-mobile {
      display: block;
    }
  }

  @media (max-width: 420px) {
    .event-card {
      flex: 0 0 calc(92%);
      max-width: 92%;
    }
    .event-card img {
      height: auto;
      aspect-ratio: 16/10;
    }
  }
</style>

<div class="page-wrapper">
  <h1>EVENTS</h1>
  <div class="events-container">
    {#each events as event}
      <a use:link href={event.link} class="event-card">
        <img src={event.img} alt={event.name} draggable="false" />
        <div class="overlay">{event.name}</div>
        <div class="event-name-mobile">{event.name}</div>
      </a>
    {/each}
  </div>
</div>
