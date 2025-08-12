<script>
  const images = [
    "/images/img1.jpg",
    "/images/img2.jpg",
    "/images/img3.jpg",
    "/images/img4.jpg",
    "/images/img5.jpg",
    "/images/img6.jpg",
    "/images/img7.jpg",
    "/images/img8.jpg",
    "/images/img9.jpg",
    "images/img10.jpg",
    "/images/img11.jpg"
  ];
</script>

<style>
  @font-face {
    font-family: 'FuturaBold';
    src: url('/FuturaBold.ttf') format('truetype');
  }

  :global(html), :global(body) {
    height: 100%;
    margin: 0;
    overflow: hidden; /* disable scroll */
  }
  .about-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding-top: 10px; /* space for navbar */
    min-height: 100vh;
    background: transparent;
    overflow-x: hidden;
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
  gap: 1.5rem;
  margin-top: -10rem; /* pull it up so it aligns with last side images */
  flex-wrap: wrap;
}

.bottom-row img {
  width: 160px; /* bigger than 140px */
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

  @media (max-width: 900px) {
    .content-wrapper {
      flex-direction: column;
      gap: 2rem;
    }
    .image-column {
      flex-direction: row;
      flex-wrap: wrap;
      justify-content: center;
    }
  }
</style>

<div class="about-container">
  <div class="content-wrapper">
    <!-- Left column -->
    <div class="image-column">
      <img src={images[0]} alt="fest" style="animation-delay: 0.1s;">
      <img src={images[1]} alt="fest" style="animation-delay: 0.3s;">
      <img src={images[2]} alt="fest" style="animation-delay: 0.5s;">
      <img src={images[3]} alt="fest" style="animation-delay: 0.7s;">
    </div>

    <!-- Text in center -->
    <div class="text-box">
      <h2>About Eureka</h2>
      <p>
        Eureka is our annual Physics Fest — a celebration of science, discovery, and innovation.  
        From mind-bending experiments to inspiring talks, we bring together curious minds and passionate souls.  
        Dive into the wonders of physics and experience the thrill of possibilities!
      </p>
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
