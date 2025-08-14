<script>
  function openPaymentSite() {
    window.open("https://southindianbank.in/ChristFee/", "_blank");
  }
  function openRegistrationSite() {
    window.open("https://docs.google.com/forms/d/e/1FAIpQLScwJ2sgGZr2wP7K9fUSeJ1cS1VYoynecos6A5tGxTiDIIZBXw/viewform", "_blank");
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
    text-align: center;
  }

  h1 {
    font-family: 'Transcity DEMO', sans-serif;
    font-size: 3rem;
    margin-bottom: 1rem;
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

  .payment-info {
    max-width: 900px;
    font-family: 'FuturaBold', sans-serif;
    font-size: 1.3rem;
    color: white;
    margin-top: 1rem;
    line-height: 1.5;
  }

  @keyframes pulseGlow {
    0%, 100% {
      box-shadow: 0 4px 15px rgba(255, 110, 196, 0.5);
    }
    50% {
      box-shadow: 0 4px 20px rgba(0, 198, 255, 0.6);
    }
  }

  @media (max-width: 768px) {
    .external-button {
      width: 80%;
      font-size: 1rem;
    }
    .payment-info {
      font-size: 0.95rem;
    }
  }

  @media (max-width: 480px) {
    .external-button {
      width: 90%;
      font-size: 0.95rem;
    }
    .payment-info {
      font-size: 0.9rem;
    }
  }
</style>

<div class="registration-container">
  <h1>Registration</h1>

  <button class="external-button" on:click={openRegistrationSite}>
    Registration Form 
  </button>

  <button class="external-button" on:click={openPaymentSite}>
    Payment
  </button>

  <p class="payment-info">
    The payment button will direct you to the Online payment portal.<br>
    Select <strong>"Fee name"</strong> → <strong>"FEST"</strong> and choose <strong>"Eureka-2025"</strong>.
  </p>
</div>
