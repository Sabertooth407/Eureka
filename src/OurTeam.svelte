
<style>
  .coming-soon-container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh; /* full height */
    color: white;
    font-family: 'Transcity DEMO', sans-serif;
    font-size: 3rem;
  }

  .dots span {
    animation: blink 1.5s infinite;
    opacity: 0;
  }

  .dots span:nth-child(1) {
    animation-delay: 0s;
  }
  .dots span:nth-child(2) {
    animation-delay: 0.3s;
  }
  .dots span:nth-child(3) {
    animation-delay: 0.6s;
  }

  @keyframes blink {
    0%, 20% { opacity: 0; }
    40%, 100% { opacity: 1; }
  }
</style>

<div class="coming-soon-container">
  Coming Soon<span class="dots">
    <span>.</span>
    <span>.</span>
    <span>.</span>
  </span>
</div>
