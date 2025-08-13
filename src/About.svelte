<script>
  import { onMount, onDestroy } from "svelte";

  const images = [
    "/img1.JPG",
    "/img2.JPG",
    "/img3.JPG",
    "/img4.JPG",
    "/img5.JPG",
    "/img6.JPG",
    "/img7.JPG",
    "/img8.JPG",
    "/img9.JPG",
    "/img10.JPG",
    "/img11.JPG"
  ];

  let carousel;
  let currentIndex = 0;
  let intervalId;

  function scrollToIndex(index) {
    if (carousel) {
      const itemWidth = carousel.offsetWidth; // one full image width
      carousel.scrollTo({
        left: index * itemWidth,
        behavior: "smooth"
      });
    }
  }

  function nextSlide() {
    currentIndex = (currentIndex + 1) % images.length;
    scrollToIndex(currentIndex);
  }

  onMount(() => {
    intervalId = setInterval(nextSlide, 3000);
    return () => clearInterval(intervalId);
  });

  onDestroy(() => clearInterval(intervalId));
</script>

<style>
  @font-face {
    font-family: 'FuturaBold';
    src: url('/FuturaBold.ttf') format('truetype');
  }

  @font-face {
    font-family: 'Transcity DEMO';
    src: url('/Transcity DEMO.otf') format('opentype');
    font-weight: bold;
    font-style: normal;
  }

  :global(html), :global(body) {
    height: 100%;
    margin: 0;
  }

  /* DESKTOP */
  .about-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding-top: 100px; /* space for navbar */
    min-height: 100vh;
    background: transparent;
    overflow-x: hidden;
  }

  .about-heading {
  font-family: 'Transcity DEMO', sans-serif;
  font-size: 3rem;
  text-align: center;
  color: white;
  margin-bottom: 0.5rem;
}

.text-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  position: relative;
  top: -90px;
}

  .content-wrapper {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 4rem;
    max-width: 1200px;
    flex-wrap: wrap;
  }

  .text-box {
    flex: 1 1 300px;
    background: rgba(0,0,0,0.6);
    padding: 2rem;
    border-radius: 1rem;
    color: white;
    font-family: 'FuturaBold', sans-serif;
    font-size: 1.2rem;
    line-height: 1.6;
    text-align: center;
    z-index: 10;
    max-width: 700px;
  }

  .image-column {
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }

  .image-column img {
    width: 140px;
    height: 140px;
    object-fit: cover;
    border-radius: 20%;
    animation: fadeInUp 1s ease forwards;
    opacity: 0;
    transform: translateY(20px);
    transition: transform 0.3s ease;
  }

  .image-column img:hover {
    transform: scale(1.05);
  }

  .bottom-row {
    display: flex;
    justify-content: center;
    gap: 5rem;
    margin-top: -10rem;
    flex-wrap: wrap;
  }

  .bottom-row img {
    width: 160px;
    height: 160px;
    object-fit: cover;
    border-radius: 20%;
    animation: fadeInUp 1s ease forwards;
    opacity: 0;
    transform: translateY(20px);
    transition: transform 0.3s ease;
  }

  .bottom-row img:hover {
    transform: scale(1.05);
  }

  @keyframes fadeInUp {
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }

  /* MOBILE CAROUSEL */
  @media (max-width: 900px) {
    .desktop-layout {
      display: none;
    }

    .carousel {
      display: flex;
      overflow: hidden; /* Only one image visible */
      width: 100%;
      height: 300px;
      position: relative;
      padding-top: 80px; /* for navbar */
    }

    .carousel img {
      flex: 0 0 100%;
      width: 100%;
      height: 100%;
      object-fit: contain;
      background: #000;
      border-radius: 0.5rem;
    }

    .mobile-about-text {
      padding: 1rem;
      text-align: center;
      font-family: 'FuturaBold', sans-serif;
      color: white;
      font-size: 1.2rem;
      line-height: 1.6;
    }
  }

  @media (min-width: 901px) {
    .carousel, .mobile-about-text {
      display: none;
    }
  }
</style>

<!-- MOBILE VIEW -->
<div class="carousel" bind:this={carousel}>
  {#each images as img}
    <img src={img} alt="fest" />
  {/each}
</div>
<div class="mobile-about-text">
  <h2>About Eureka</h2>
  <p>
    Eureka is our annual Physics Fest — a celebration of science, discovery, and innovation.
    From mind-bending experiments to inspiring talks, we bring together curious minds and passionate souls.
    Dive into the wonders of physics and experience the thrill of possibilities!
  </p>
</div>

<!-- DESKTOP VIEW -->
<div class="desktop-layout">
  <div class="about-container">
    <div class="content-wrapper">
      <!-- Left column -->
      <div class="image-column">
        <img src={images[0]} alt="fest" style="animation-delay: 0.1s;">
        <img src={images[1]} alt="fest" style="animation-delay: 0.3s;">
        <img src={images[2]} alt="fest" style="animation-delay: 0.5s;">
        <img src={images[3]} alt="fest" style="animation-delay: 0.7s;">
      </div>

      <!-- Heading OUTSIDE the text box -->
      <div class="text-section">
        <h2 class="about-heading">About Eureka</h2>
        <div class="text-box">
          <p>
            Eureka is our annual Physics Fest — a celebration of science, discovery, and innovation.
            From mind-bending experiments to inspiring talks, we bring together curious minds and passionate souls.
            Dive into the wonders of physics and experience the thrill of possibilities!
          </p>
        </div>
      </div>

      <!-- Right column -->
      <div class="image-column">
        <img src={images[4]} alt="fest" style="animation-delay: 0.2s;">
        <img src={images[5]} alt="fest" style="animation-delay: 0.4s;">
        <img src={images[6]} alt="fest" style="animation-delay: 0.6s;">
        <img src={images[7]} alt="fest" style="animation-delay: 0.8s;">
      </div>
    </div>

    <!-- Bottom images -->
    <div class="bottom-row">
      <img src={images[8]} alt="fest" style="animation-delay: 0.3s;">
      <img src={images[9]} alt="fest" style="animation-delay: 0.5s;">
      <img src={images[10]} alt="fest" style="animation-delay: 0.7s;">
    </div>
  </div>
</div>

