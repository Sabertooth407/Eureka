<script>
  const eventDescription = `
    A Model United Nations set in 1946, delegates debate nuclear control after Hiroshima and Nagasaki, 
    drafting resolutions to shape the atomic age.
  `;

  const prelimsLink = "https://forms.gle/sCMLGWznD83xwRNV6"; // Replace with actual form link

  const rounds = [
    {
      title: "Preliminary Round (Online Submission)",
      details: [
        `Submit a 500–800 word policy statement detailing your country’s stance on the agenda, rooted in the historical context and national priorities of 1946.`,
        `Format: PDF, Times New Roman, 12 pt, 1.5 spacing.`,
        `All delegates will be writing their online submission for the country: CANADA.`,
        `Submit your entry here: <a href="${prelimsLink}" target="_blank" rel="noopener noreferrer" class="link-btn">Prelims Submission Form</a>`
      ]
    },
    {
      title: "Final Round (On-Campus MUN Session)",
      details: [
        "Shortlisted participants will represent countries assigned by the organisers (which may differ from prelim submission).",
        "Proceedings follow official MUN protocol — moderated/unmoderated caucuses, working paper & draft resolution creation, and voting.",
        "Judging based on historical accuracy, diplomatic strategy, depth of knowledge, and engagement in debate."
      ]
    }
  ];

  const awards = [
    "Best Delegate – ₹2500",
    "High Commendation – ₹1500"
  ];

  const pdfUrl = "/PHYMUNrules.pdf"; // your uploaded PDF path
</script>

<style>
  .mun-container {
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

  .section {
    background: rgba(255, 255, 255, 0.05);
    padding: clamp(1rem, 2.5vw, 1.5rem);
    border-radius: 12px;
    margin-bottom: 1.5rem;
    transition: transform 0.25s ease, box-shadow 0.25s ease;
  }

  @media (hover: hover) {
    .section:hover {
      transform: translateY(-3px);
      box-shadow: 0 0 20px rgba(255, 110, 196, 0.3);
    }
  }

  .section h2 {
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

  /* Styled link button inside text */
  .link-btn {
    color: #ff6ec4;
    font-weight: bold;
    text-decoration: underline;
    transition: color 0.25s ease;
  }

  .link-btn:hover {
    color: white;
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

<div class="mun-container">
  <!-- Desktop PDF button -->
  <a href={pdfUrl} target="_blank" rel="noopener noreferrer" class="rules-btn-desktop">
    Rules PDF
  </a>

  <h1>PHYMUN</h1>

  <!-- Mobile PDF button -->
  <a href={pdfUrl} target="_blank" rel="noopener noreferrer" class="rules-btn-mobile">
    Rules PDF
  </a>

  <p class="description">{eventDescription}</p>

  {#each rounds as round}
    <div class="section">
      <h2>{round.title}</h2>
      <ul>
        {#each round.details as detail}
          <li>{@html detail}</li> <!-- Use @html to render link -->
        {/each}
      </ul>
    </div>
  {/each}

  <div class="section">
    <h2>Awards</h2>
    <ul>
      {#each awards as award}
        <li>{award}</li>
      {/each}
    </ul>
  </div>
</div>
