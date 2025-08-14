<script>
  const eventDescription = `
    Make physics fun in Newton’s Meme-athon! From emoji-based guessing games to physics charades and meme-powered explanations, this event brings creativity and humor into the world of physics.
  `;

  const rounds = [
    {
      title: "Preliminary Round",
      details: [
        "Guess the physics phenomenon or physicist from emojis, GIFs, or pictures.",
        "Answers are written on A4 sheets.",
        "Teams with the highest number of correct answers qualify for the main round."
      ]
    },
    {
      title: "First Round",
      details: [
        "Teams pick a chit to decide their mode: Dumb Charades or Draw & Guess.",
        "Pick another chit to decide the concept/phenomenon.",
        "Charades: Act without speaking; no hints.",
        "Draw & Guess: Draw without letters, numbers, or words.",
        "Each team gets 30–60 seconds per concept.",
        "Tie-breaker: Team that guesses in less time wins."
      ]
    },
    {
      title: "Final Round",
      details: [
        "Teams choose a physics topic and explain it using memes or humorous language.",
        "Judging criteria: understanding, humor, creativity.",
        "Presentation required.",
        "Judges' decision is final."
      ]
    }
  ];

  const pdfUrl = "/NEWTON’S MEME-ATHON.pdf"; // Replace with actual path
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
    h1 {
      font-size: 3rem;
    }
  }
</style>

<div class="maze-container">
  <a href={pdfUrl} target="_blank" rel="noopener noreferrer" class="rules-btn-desktop">
    Rules PDF
  </a>

  <h1>Newton’s Meme-athon</h1>

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
    <p>Teams may consist of 2–3 members.</p>
  </div>

  <div class="round">
    <h2>General Rules</h2>
    <ul>
      <li>No mobile phones, internet, or external help.</li>
      <li>Judges' and event heads' decisions are final.</li>
      <li>Maintain fair play and respect time limits.</li>
      <li>No copying answers; leads to disqualification.</li>
    </ul>
  </div>
</div>
