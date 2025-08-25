<script>
  // Example results – replace with real data
  const results = [
  {
      event: "PhyMUN",
      winner: { name: "PRANJAL RAWAT, PRATYUSH", university: "CHRIST UNIVERSITY" }
    },  
  {
      event: "Oblivion",
      first: { name: "Arpan Chakrabarty , Aaron V Nandiha, Nithin S Urs", university: "CHRIST UNIVERSITY" },
      second: { name: "Aanishka Barua , Avani Navada , Saif Kandarumadathil Nysal", university: "ST.JOSEPH'S UNIVERSITY" }
    },
    {
      event: "Tri-Physics Tournament",
      first: { name: "Sanjay MV , Shakti Aishvaryar , Aniruddha Srivasthava K", university: "ST.JOSEPH'S UNIVERSITY" },
      second: { name: "Disha Anne Aaria, Hrt , Saif", university: "ST.JOSEPH'S UNIVERSITY" }
    },
    {
      event: "Ad Astra Abyssoque",
      first: { name: "Kevin K Mathew Chittoor, Rohini G Acharya, Vaishnavi Kasturirangan", university: "ST.JOSEPH'S UNIVERSITY" },
      second: { name: "Donlunching, Krutika Zambre, Aniketh Anil", university: "CHRIST UNIVERSITY" }
    },
    {
      event: "The Physicist's Code",
      first: { name: "Sanjay M V, Shakti Aishvarya R S, Aniruddha Srivasthava K", university: "ST.JOSEPH'S UNIVERSITY" },
      second: { name: "S.A Ashish Dixit, Ruben Mundu, Yash Shashikanth", university: "ST.JOSEPH'S UNIVERSITY" }
    },
    {
      event: "Newton's Meme-athon",
      first: { name: "Vaishnavi K.R, Kevin C Matthew, Rohini G Acharya", university: "ST.JOSEPH'S UNIVERSITY " },
      second: { name: "Pooja Kumari S, Tuhin Adhikari, Anurag Atta", university: "ST.JOSEPH'S UNIVERSITY " }
    },
    {
      event: "Maze Frenzy",
      first: { name: "Anmol Harshit Minj, Bhargav Bhat", university: "ST.JOSEPH'S UNIVERSITY" },
      second: { name: "Sanjana Rachel, Shreya Narayana Murthy, Ananya ", university: "ST.JOSEPH'S UNIVERSITY" }
    }
  ];

  const bestUni = {
    name: "St. Joseph's University",
    img: "/winners.jpg" // put this image in `static/`
  };
</script>

<style>
  .results-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 2rem;
    color: white;
    min-height: 100vh;
  }

  h1 {
    font-family: 'Transcity DEMO', sans-serif;
    font-size: 3rem;
    margin-bottom: 2rem;
    color: white;
    text-align: center;
  }

  .event-block {
    width: 90%;
    max-width: 800px;
    background: rgba(0, 0, 0, 0.6);
    margin: 1rem 0;
    padding: 1.5rem;
    border-radius: 12px;
    box-shadow: 0 0 15px rgba(255, 110, 196, 0.4);
    text-align: center;
    font-family: 'FuturaBold', sans-serif;
  }

  .event-title {
    font-size: 1.5rem;
    margin-bottom: 1rem;
    color:white;
  }

  .placement {
    margin: 0.3rem 0;
    font-size: 1.1rem;
  }

  .first {
    color: gold;
  }

  .second {
    color: silver;
  }

  .winner {
    color: gold;
    font-weight: bold;
  }

  /* Best Uni */
  .best-uni {
    margin-top: 3rem;
    text-align: center;
  }

  .best-uni h1 {
    font-size: 2.5rem;
    color: white;
    margin-bottom: 1rem;
    font-family: 'Transcity DEMO', sans-serif;
  }

  .best-uni img {
    max-width: 700px;
    width: 90%;
    border-radius: 12px;
    box-shadow: 0 0 25px rgba(0, 198, 255, 0.6);
    margin-top: 1rem;
  }
</style>

<div class="results-container">
  <h1>Event Results</h1>

  {#each results as row}
    <div class="event-block">
      <div class="event-title">{row.event}</div>

      {#if row.winner}
        <div class="placement winner">Winner:  {row.winner.name} ({row.winner.university})</div>
      {:else}
        <div class="placement first">First: {row.first.name} — {row.first.university}</div>
        <div class="placement second">Runner Up: {row.second.name} — {row.second.university}</div>
      {/if}
    </div>
  {/each}

  <!-- Best University -->
  <div class="best-uni">
    <h1>Winners of Eureka 2025</h1>
    <h2>{bestUni.name}</h2>
    <img src={bestUni.img} alt="Best University" />
  </div>
</div>
