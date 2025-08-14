<script>
  const eventDescription = `
    Think fast and move faster in Maze Frenzy, the ultimate mix of brainpower and reflexes! 
    A fast-paced mix of word search, memory-based circuit solving, and a physical maze with strategic challenges.
  `;

  const rounds = [
    {
      title: "Round 1: Word Search (Prelims)",
      details: [
        "Find words hidden in a grid using the hints provided.",
        "Each clue corresponds to a physics-related term hidden in the puzzle.",
        "15 minutes time limit.",
        "Top 6 teams with most correct words qualify."
      ]
    },
    {
      title: "Round 2: Circuit Solving (5 mins)",
      details: [
        "Test memory & understanding by solving basic circuit problems.",
        "See a circuit for 30 seconds → Recreate from memory & solve.",
        "Allowed formulas: Ohm’s Law, Kirchhoff’s laws, etc.",
        "Top 3 fastest & most accurate teams move to final."
      ]
    },
    {
      title: "Final Round: Maze Game",
      details: [
        "Navigate a cardboard maze using a magnet to move an iron ball.",
        "Checkpoints inside maze → Answer physics questions.",
        "Start with 100 Maze Points (MP) for dares & path checks.",
        "First to exit or farthest with most points wins."
      ]
    }
  ];

  const pdfUrl = "/Maze Frenzy Rules.pdf"; // change to your actual file path
</script>

<style>
  .maze-container {
    max-width: 1000px;
    margin: auto;
    color: white;
    font-family: Arial, sans-serif;
    position: relative;
  }

  h1 {
    font-family: 'Transcity DEMO', sans-serif;
    font-size: clamp(2rem, 5vw, 3rem);
    text-align: center;
    margin-bottom: 0.5rem;
  }

  /* Desktop top-right button */
  .rules-btn-desktop {
    position: absolute;
    top: 1rem;
    right: 1rem;
    padding: 0.5rem 1rem;
    border: 2px solid #ff6ec4;
    border-radius: 8px;
    background: transparent;
    color: #ff6ec4;
    font-weight: bold;
    text-decoration: none;
    transition: all 0.25s ease;
  }

  .rules-btn-desktop:hover {
    background: rgba(255, 110, 196, 0.1);
    transform: translateY(-2px);
    box-shadow: 0 4px 12px rgba(255, 110, 196, 0.3);
  }

  /* Mobile button under event name */
  .rules-btn-mobile {
    display: none;
    margin: 0.5rem auto 1.5rem auto;
    padding: 0.5rem 1rem;
    border: 2px solid #ff6ec4;
    border-radius: 8px;
    background: transparent;
    color: #ff6ec4;
    font-weight: bold;
    text-decoration: none;
    text-align: center;
    width: fit-content;
    transition: all 0.25s ease;
  }

  .rules-btn-mobile:hover {
    background: rgba(255, 110, 196, 0.1);
  }

  .description {
    font-size: clamp(1rem, 2.5vw, 1.1rem);
    text-align: center;
    margin-bottom: 2rem;
    line-height: 1.5;
    font-family: 'Futura', sans-serif;
  }

  .round {
    background: rgba(255, 255, 255, 0.05);
    padding: clamp(1rem, 2.5vw, 1.5rem);
    border-radius: 12px;
    margin-bottom: 1.5rem;
    transition: transform 0.25s ease, box-shadow 0.25s ease;
  }

  @media (hover: hover) {
    .round:hover {
      transform: translateY(-3px);
      box-shadow: 0 0 20px rgba(255, 110, 196, 0.3);
    }
  }

  .round h2 {
    color: #ff6ec4;
    font-size: clamp(1.2rem, 3vw, 1.5rem);
    margin-bottom: 0.5rem;
  }

  ul {
    padding-left: 1.2rem;
  }

  li {
    margin: 0.4rem 0;
    font-size: clamp(0.95rem, 2.3vw, 1rem);
  }

  p {
    font-size: clamp(0.95rem, 2.3vw, 1rem);
  }

  @media (max-width: 768px) {
    .rules-btn-desktop {
      display: none;
    }
    .rules-btn-mobile {
      display: block;
    }
    ul {
      padding-left: 1rem;
    }
    h1{
        font-size: 3rem;
    }
  }
</style>

<div class="maze-container">
  <!-- Desktop button -->
  <a href={pdfUrl} target="_blank" rel="noopener noreferrer" class="rules-btn-desktop">
    Rules PDF
  </a>

  <h1>Maze Frenzy</h1>

  <!-- Mobile button -->
  <a href={pdfUrl} target="_blank" rel="noopener noreferrer" class="rules-btn-mobile">
    Rules PDF
  </a>

  <p class="description">{eventDescription}</p>

  {#each rounds as round}
    <div class="round">
      <h2>{round.title}</h2>
      <ul>
        {#each round.details as detail}
          <li>{detail}</li>
        {/each}
      </ul>
    </div>
  {/each}

  <div class="round">
    <h2>Team Structure</h2>
    <p>Each team consists of 2 participants.</p>
  </div>

  <div class="round">
    <h2>Winning Criteria</h2>
    <ul>
      <li>First to exit the maze or cover the most ground in the least time with most correct answers wins.</li>
      <li>In case of tie → team with more Maze Points left wins.</li>
      <li>10 Maze Points = 1 minute time reduction.</li>
    </ul>
  </div>
</div>
