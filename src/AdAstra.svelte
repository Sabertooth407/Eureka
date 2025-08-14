<script>
  const eventDescription = `
    “To the Stars and the Abyss” — Ad Astra Abyssoque is a physics-powered strategy challenge 
    where problem-solving meets resource trading.
  `;

  const rounds = [
    {
      title: "Round 1: Prelims",
      details: [
        "Teams solve a set of challenging physics problems.",
        "Questions test analytical skills, logical reasoning, and conceptual clarity.",
        "Top teams qualify for the final based on accuracy and speed."
      ]
    },
    {
      title: "Final Round: Strategy & Trade",
      details: [
        "Teams participate in a resource-based strategy simulation.",
        "Use problem-solving to earn, trade, and manage resources.",
        "Physics knowledge directly influences the outcome of negotiations.",
        "Team with best strategy and resource management wins."
      ]
    }
  ];

  const pdfUrl = "/Ad_Astra_Abyssoque.pdf"; // Change to actual path
</script>

<style>
  .event-container {
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

  /* Desktop button */
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

  /* Mobile button */
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

<div class="event-container">
  <!-- Desktop PDF Button -->
  <a href={pdfUrl} target="_blank" rel="noopener noreferrer" class="rules-btn-desktop">
    Rules PDF
  </a>

  <h1>Ad Astra Abyssoque</h1>

  <!-- Mobile PDF Button -->
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
    <p>Teams of 2–3 participants.</p>
  </div>

  <div class="round">
    <h2>Winning Criteria</h2>
    <ul>
      <li>Highest final score after trading and challenge rounds wins.</li>
      <li>In case of tie → fastest completion of challenges decides.</li>
    </ul>
  </div>
</div>
