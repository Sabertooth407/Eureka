<script>
  const eventDescription = `
    A three-round physics challenge combining quizzes, creative puzzles, and a practical optics test. 
    From rapid-fire questions to physics Pictionary and a laser path race, teams need both knowledge and skill to win.
  `;

  const rounds = [
    {
      title: "Round 1: The OWLS (Quiz Competition)",
      details: [
        "Written-based quiz focused on core physics concepts.",
        "Multiple choice, audiovisual, and conceptual questions.",
        "Duration: 10 minutes.",
        "Focus areas: Mechanics, Thermodynamics, Electromagnetism, Modern Physics.",
        "Top teams proceed to the next round."
      ]
    },
    {
      title: "Round 2: Riddikulus (Physics Pictionary)",
      details: [
        "One member draws a physics concept while others guess.",
        "No letters, numbers, or speaking allowed.",
        "Whiteboard or chart-based drawing.",
        "Duration: 20 minutes (3 minutes per team + buffer).",
        "Top 4 teams advance to the final."
      ]
    },
    {
      title: "Round 3: Lumos Maxima (Laser Path Challenge)",
      details: [
        "Align four mirrors to direct a fixed laser beam onto a target.",
        "Foam blocks serve as obstacles.",
        "Materials provided: Laser, mirrors, target board.",
        "Duration: 5 minutes max.",
        "Fastest and most accurate team wins."
      ]
    }
  ];

  const pdfUrl = "/The Tri Physics Tournament.pdf"; // link to the uploaded rules PDF
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
    h1 {
      font-size: 3rem;
    }
  }
</style>

<div class="maze-container">
  <!-- Desktop button -->
  <a href={pdfUrl} target="_blank" rel="noopener noreferrer" class="rules-btn-desktop">
    Rules PDF
  </a>

  <h1>The Tri-Physics Tournament</h1>

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
    <p>Each team must consist of 3 participants.</p>
  </div>

  <div class="round">
    <h2>Evaluation Criteria</h2>
    <ul>
      <li>Accuracy and correctness in each round.</li>
      <li>Time management and efficiency.</li>
      <li>Team coordination and strategy.</li>
      <li>Conceptual understanding of physics principles.</li>
    </ul>
  </div>
</div>
