<script>
  import { onMount } from 'svelte';
  import { goto } from '$app/navigation';

  const targetDate = new Date(2025, 7, 22, 0, 0, 0).getTime();

  let days = '00', hours = '00', minutes = '00', seconds = '00';
  let eventStarted = false;

  function pad(num) {
    return String(num).padStart(2, '0');
  }

  function updateTimer() {
    const now = new Date().getTime();
    const distance = targetDate - now;

    if (distance <= 0) {
      eventStarted = true;
      return;
    }

    days = pad(Math.floor(distance / (1000 * 60 * 60 * 24)));
    hours = pad(Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60)));
    minutes = pad(Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60)));
    seconds = pad(Math.floor((distance % (1000 * 60)) / 1000));
  }

  onMount(() => {
    updateTimer();
    const interval = setInterval(updateTimer, 1000);
    return () => clearInterval(interval);
  });

  const instagramUrl = "https://www.instagram.com/eureka_2025.pa?utm_source=ig_web_button_share_sheet&igsh=MWUwdmF0OGFvMWxydA==";
  const linkedinUrl = "https://linkedin.com/company/department-of-physics-electronics";
</script>

<style>
@font-face {
  font-family: 'FuturaBold';
  src: url('/FuturaBold.ttf') format('truetype');
}

.home {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: calc(100vh - 110px);
  padding-top: 15px;
  text-align: center;
  padding-left: 1rem;
  padding-right: 1rem;
  box-sizing: border-box;
}

/* Logo scaling */
img {
  max-width: 90%;
  width: clamp(150px, 30vw, 300px);
  height: auto;
  margin-bottom: 1rem;
  animation: glowPulse 2.5s ease-in-out infinite;
  filter: drop-shadow(-5px 0 10px rgba(160, 32, 240, 0.6))
          drop-shadow(5px 0 10px rgba(0, 200, 255, 0.6));
}

@keyframes glowPulse {
  0%, 100% {
    filter: drop-shadow(-5px 0 10px rgba(160, 32, 240, 0.6))
            drop-shadow(5px 0 10px rgba(0, 200, 255, 0.6));
  }
  50% {
    filter: drop-shadow(-8px 0 15px rgba(160, 32, 240, 1))
            drop-shadow(8px 0 15px rgba(0, 200, 255, 1));
  }
}

/* Timer text */
.timer {
  font-size: clamp(1.5rem, 4vw, 2.5rem);
  margin-top: 1rem;
  font-weight: bold;
  font-family: 'FuturaBold', sans-serif;
  color: white;
}

/* Tagline */
.tagline {
  font-size: clamp(1.2rem, 3vw, 2rem);
  margin-top: 0.5rem;
  color: #ffffff;
  font-family: 'FuturaBold', sans-serif;
  max-width: 90%;
}

/* Social icons */
.social-icons {
  display: flex;
  gap: clamp(0.8rem, 3vw, 1.5rem);
  margin-top: 1.5rem;
  justify-content: center;
  flex-wrap: wrap;
}

.social-icons a {
  display: flex;
  align-items: center;
  justify-content: center;
  transition: transform 0.25s ease;
}

.social-icons a:hover {
  transform: scale(1.2);
}

.brochure-btn {
  padding: 0.5rem 1rem;
  font-weight: bold;
  border: 2px solid #ff6ec4;
  border-radius: 8px;
  background: transparent;
  color: #ff6ec4;
  text-decoration: none;
  transition: all 0.25s ease;
}

.brochure-btn:hover {
  transform: translateY(-2px) scale(1.03);
  box-shadow: 0 4px 15px rgba(255, 110, 196, 0.3);
}

/* Icon size scales with screen */
.social-icons svg {
  width: clamp(24px, 4vw, 36px);
  height: clamp(24px, 4vw, 36px);
}
/* Mobile-only buttons */
.mobile-buttons {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  margin-top: 2rem;
}

.mobile-buttons a {
  text-decoration: none;
}

.mobile-buttons button {
  width: 100%;
  padding: 0.75rem 1.5rem;
  font-size: 1.1rem;
  font-weight: bold;
  border: 2px solid #ff6ec4; /* Pinkish border */
  border-radius: 12px; /* Rounded rectangle */
  background: transparent; /* No fill */
  color: #ff6ec4; /* Matching text color */
  cursor: pointer;
  box-shadow: 0 4px 15px rgba(0,0,0,0.1);
  transition: all 0.25s ease;
  animation: pulseGlow 3s infinite;
}

.mobile-buttons button:hover {
  transform: translateY(-2px) scale(1.03);
  box-shadow: 0 6px 20px rgba(255, 110, 196, 0.3);
}

.mobile-buttons button:active {
  transform: scale(0.95);
  box-shadow: 0 2px 10px rgba(255, 110, 196, 0.4);
  background: rgba(255, 110, 196, 0.1); /* subtle click fill */
}



/* Pulse glow stays */
@keyframes pulseGlow {
  0%, 100% {
    box-shadow: 0 4px 15px rgba(255, 110, 196, 0.5);
  }
  50% {
    box-shadow: 0 4px 20px rgba(0, 198, 255, 0.6);
  }
}

/* Hide mobile buttons on desktop */
@media (min-width: 769px) {
  .mobile-buttons {
    display: none;
  }
}
@media (max-width: 768px) {
  img {
    width: clamp(200px, 50vw, 350px); /* Bigger width for phones */
    max-width: 100%;
  }
  .brochure-btn{
    display: none !important;
  }
}
</style>

<div class="home">
  <img src="/logo.png" alt="Eureka" />

  {#if eventStarted}
    <div class="timer">Welcome to Eureka 2025</div>
  {:else}
    <div class="timer">
      {days}D {hours}H {minutes}M {seconds}S
    </div>
  {/if}

  <div class="tagline">
    Where Every Possibility Has A Probability
  </div>

  <!-- Social icons -->
  <div class="social-icons">
    <a href={instagramUrl} target="_blank" rel="noopener noreferrer" aria-label="Instagram">
      <!-- Instagram SVG -->
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="white">
        <path d="M12 2.163c3.204 0 3.584.012 4.85.07 
          1.17.056 1.97.24 2.428.403a4.92 4.92 0 011.77 1.145 
          4.92 4.92 0 011.145 1.77c.163.458.347 1.258.403 
          2.428.058 1.266.07 1.646.07 4.85s-.012 3.584-.07 
          4.85c-.056 1.17-.24 1.97-.403 2.428a4.92 4.92 0 
          01-1.145 1.77 4.92 4.92 0 01-1.77 1.145c-.458.163-1.258.347-2.428.403
          -1.266.058-1.646.07-4.85.07s-3.584-.012-4.85-.07
          c-1.17-.056-1.97-.24-2.428-.403a4.92 4.92 0 
          01-1.77-1.145 4.92 4.92 0 01-1.145-1.77c-.163-.458-.347-1.258-.403
          -2.428C2.175 15.747 2.163 15.367 2.163 
          12s.012-3.584.07-4.85c.056-1.17.24-1.97.403-2.428a4.92
          4.92 0 011.145-1.77 4.92 4.92 0 011.77-1.145c.458-.163 
          1.258-.347 2.428-.403C8.416 2.175 8.796 2.163 12 
          2.163zm0 1.837c-3.17 0-3.548.012-4.795.07-1.026.047-1.58.218-1.948.363a3.09
          3.09 0 00-1.124.73 3.09 3.09 0 00-.73 1.124c-.145.368-.316.922-.363 
          1.948-.058 1.247-.07 1.625-.07 4.795s.012 3.548.07 4.795c.047 
          1.026.218 1.58.363 1.948.168.427.39.78.73 1.124.344.34.697.562 
          1.124.73.368.145.922.316 1.948.363 1.247.058 1.625.07 
          4.795.07s3.548-.012 4.795-.07c1.026-.047 1.58-.218 
          1.948-.363a3.09 3.09 0 001.124-.73 3.09 3.09 0 
          00.73-1.124c.145-.368.316-.922.363-1.948.058-1.247.07-1.625.07
          -4.795s-.012-3.548-.07-4.795c-.047-1.026-.218-1.58-.363
          -1.948a3.09 3.09 0 00-.73-1.124 3.09 3.09 0 
          00-1.124-.73c-.368-.145-.922-.316-1.948-.363-1.247-.058
          -1.625-.07-4.795-.07zm0 3.915a5.922 5.922 0 
          110 11.844 5.922 5.922 0 010-11.844zm0 1.837a4.085 
          4.085 0 100 8.17 4.085 4.085 0 000-8.17zm6.406-2.845a1.44 
          1.44 0 110 2.881 1.44 1.44 0 010-2.881z"/>
      </svg>
    </a>

    <a href={linkedinUrl} target="_blank" rel="noopener noreferrer" aria-label="LinkedIn">
      <!-- LinkedIn SVG -->
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="white">
        <path d="M20.447 20.452H16.89v-5.569c0-1.328-.026-3.037-1.852-3.037
          -1.853 0-2.136 1.445-2.136 2.939v5.667H9.342V9h3.4v1.561h.047c.474
          -.9 1.63-1.85 3.355-1.85 3.584 0 4.247 2.358 4.247 5.423v6.318zM5.337 
          7.433a1.97 1.97 0 11.001-3.94 1.97 1.97 0 01-.001 3.94zM6.813 
          20.452H3.861V9h2.952v11.452zM22.225 0H1.771C.792 
          0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 
          24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 
          .774 23.2 0 22.225 0z"/>
      </svg>
    </a>
    <a href="/brochure.pdf" target="_blank" rel="noopener noreferrer" class="brochure-btn">
    Brochure
  </a>
  </div>

  <!-- Mobile-only navigation buttons -->
  <div class="mobile-buttons">
    <a href="/#/about">
    <button>About</button>
  </a>
  <a href="/#/registration">
    <button>Register</button>
  </a>
   <a href="/#/events">
    <button>Events</button>
  </a>
  <a href="/#/contact">
    <button>Contact</button>
  </a>
  <a href="/brochure.pdf" target="_blank" rel="noopener noreferrer">
    <button>Brochure</button>
  </div>
</div>
