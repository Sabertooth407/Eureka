<script>
  const row1 = [
    "Y. Srivathsa",
    "Aayush Rai",
    "Mohith Nigam",
    "Kishan Jaiganesh",
    "Soham Sarkar",
    "Jeril",
    "Anzer M"
  ];
  const row2 = [
    "Kanak Wasnik",
    "Anokha Ramesh",
    "Ashika K J",
    "Melonee M",
    "Ekjot",
    "Akshatha",
    "Aarya Sajayan",
    "Preksha"
  ];
</script>

<style>
  .team-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: flex-start;
    min-height: 100vh;
    color: white;
    text-align: center;
    padding: 1rem;
  }

  h1 {
    font-family: 'Transcity DEMO', sans-serif;
    font-size: 3rem;
    margin-bottom: 1rem;
    color: white;
  }

  img {
    max-width: 600px;
    width: 90%;
    border-radius: 1rem;
    margin-bottom: 2rem;
    box-shadow: 0 0 20px rgba(255, 110, 196, 0.5);
  }

  .names-row {
    font-family: 'FuturaBold', sans-serif;
    font-size: 1rem;
    border: 1px solid #ff6ec4;
    border-radius: 8px;
    background: rgba(255, 110, 196, 0.1);
    padding: 1rem;
    margin: 0.5rem 0;
    width: 100%;
    max-width: 1000px;
    word-wrap: break-word;
    line-height: 1.6;
  }

  /* Responsive tweaks */
  @media (max-width: 768px) {
    h1 {
      font-size: 3rem;
    }
    .names-row {
      font-size: 1rem;
      padding: 0.8rem;
    }
    img {
      max-width: 100%;
    }
  }

  @media (max-width: 480px) {
    h1 {
      font-size: 3rem;
    }
    .names-row {
      font-size: 0.9rem;
      padding: 0.6rem;
    }
  }
</style>

<div class="team-container">
  <h1>Our Team</h1>

  <!-- Middle picture -->
  <img src="/team.JPG" alt="Our Team" />

  <!-- Names combined -->
  <div class="names-row">
    Row 1 (Left to Right) 
    <br>
    {row1.join(", ")}
    <br/><br/>
    Row 2 (Left to Right)
    <br>{row2.join(", ")}
  </div>
</div>
