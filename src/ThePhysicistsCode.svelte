<script>
  const eventDescription = `
    A multi-stage mystery where physics case
studies and a hunt to reveal digits of a
secret code. Crack them all to unlock the
final challenge.
  `;

  const rounds = [
    {
      title: 'Round 1: The Anomaly Report',
      details: [
        'Theme: Dimensional Analysis + Experimental Physics (Case-Based)',
        'Identify all dimensional inconsistencies in given equations.',
        'Spot at least two violations of thermodynamic laws.',
        'Find the log entry showing a calibration error.',
        'Code Digit 1: Units digit of the total inconsistencies correctly identified (out of 7).'
      ]
    },
    {
      title: 'Round 2: Relativity of Silence',
      details: [
        'Theme: Special Relativity + Signal Delay (Case-Based)',
        'Analyze simultaneity using Lorentz transformations.',
        'Identify frame where events appear simultaneous.',
        'Calculate proper time and determine correct frame.',
        'Code Digit 2: Units digit of the relative velocity (% of c) of that frame.'
      ]
    },
    {
      title: 'Round 3: The Gravity Vault',
      details: [
        'Theme: Advanced Gravitation + Energy Conservation (Case-Based)',
        'Model gravitational field variation on an exoplanet.',
        'Check if potential energy curve suggests dark matter-like core.',
        'Calculate escape energy required from 5 km depth.',
        'Code Digit 3: Units digit of the energy in MJ required.'
      ]
    },
    {
      title: 'Round 4: The Quantum Archive',
      details: [
        'Theme: Quantum Transitions + Spectroscopy (Case-Based)',
        'Identify possible transitions and initial states from wavelength data.',
        'Use Rydberg equation for multielectron ions.',
        'Estimate quantum defect.',
        'Code Digit 4: Integer part of estimated quantum defect.'
      ]
    },
    {
      title: 'Round 5: The Lost Coordinates',
      details: [
        'Theme: Campus-Based Physics Treasure Hunt',
        'Solve physics riddles to find locations.',
        'Each correct location reveals clues or QR codes with code digits.',
        'Code Digit 5: Found within QR codes/clues.'
      ]
    }
  ];

  const pdfUrl = "/PhysicistsCodeRules.pdf";
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

<div class="maze-container">
  <a href={pdfUrl} target="_blank" rel="noopener noreferrer" class="rules-btn-desktop">
    Rules PDF
  </a>

  <h1>The Physicist's Code</h1>

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
    <p>Individual event. No mobile phones, electronic gadgets, or calculators allowed. Decision of the Event Head is final.</p>
  </div>
</div>
