<!--<script>
  function openExternalSite() {
    window.open("https://southindianbank.in/ChristFee/", "_blank");
  }
</script>

<style>
  @font-face {
    font-family: 'FuturaBold';
    src: url('/FuturaBold.ttf') format('truetype');
  }

  .registration-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    min-height: 100vh;
    padding: 1rem;
  }

  h1 {
    font-family: 'Transcity DEMO', sans-serif;
    font-size: 3rem;
    margin-bottom: 1rem;
    text-align: center;
  }

  .external-button {
    width: 20%;
    padding: 0.75rem 1.5rem;
    font-size: 1.1rem;
    font-weight: bold;
    border: 2px solid #ff6ec4;
    border-radius: 12px;
    background: transparent;
    color: #ff6ec4;
    cursor: pointer;
    box-shadow: 0 4px 15px rgba(0,0,0,0.1);
    transition: all 0.25s ease;
    animation: pulseGlow 3s infinite;
    margin-bottom: 1.5rem;
    text-align: center;
  }

  .external-button:hover {
    transform: translateY(-2px) scale(1.03);
    box-shadow: 0 6px 20px rgba(255, 110, 196, 0.3);
  }

  .external-button:active {
    transform: scale(0.95);
    box-shadow: 0 2px 10px rgba(255, 110, 196, 0.4);
    background: rgba(255, 110, 196, 0.1);
  }

  @keyframes pulseGlow {
    0%, 100% {
      box-shadow: 0 4px 15px rgba(255, 110, 196, 0.5);
    }
    50% {
      box-shadow: 0 4px 20px rgba(0, 198, 255, 0.6);
    }
  }

  iframe {
    width: 100%;
    max-width: 900px;
    height: 90vh;
    border: none;
    border-radius: 8px;
    background-color: transparent;
  }

  @media (max-width: 768px) {
    h1 {
      font-size: 3rem;
    }

    .external-button {
      width: 80%;
      font-size: 1rem;
    }

    iframe {
      height: 100vh;
      width: 100vw;
    }
  }

  @media (max-width: 480px) {
    .external-button {
      width: 90%;
      font-size: 0.95rem;
    }

    h1 {
      font-size: 3rem;
    }
  }
</style>

<div class="registration-container">
  <h1>Registration</h1>

  <button class="external-button" on:click={openExternalSite}>
    Payment
  </button>

  <iframe
    src="https://docs.google.com/forms/d/e/1FAIpQLScQwGSpVxrF9iOwspQq25QpIhLb8OfhNQ5EqHCUMsLZGzc6-A/viewform?embedded=true"
    allowfullscreen>
  </iframe>
</div>
-->

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
