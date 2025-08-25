<script>
  let selectedPhoto = null; // state for clicked photo

  const videoUrl = "/aftermovie.mov"; 
  const photos = [
    "/gallery/1.jpg",
    "/gallery/2.jpg",
    "/gallery/3.jpg",
    "/gallery/4.jpg",
    "/gallery/5.jpg",
    "/gallery/6.jpg",
    "/gallery/7.jpg",
    "/gallery/8.jpg",
    "/gallery/9.jpg",
    "/gallery/10.jpg",
    "/gallery/11.jpg",
    "/gallery/12.jpg",
    "/gallery/13.jpg",
    "/gallery/14.jpg",
    "/gallery/15.jpg"
  ];
</script>

<style>
  .gallery-container {
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

  .video-highlight {
    width: 100%;
    max-width: 500px;
    margin-bottom: 3rem;
    border-radius: 1rem;
    overflow: hidden;
    box-shadow: 0 0 25px rgba(255, 110, 196, 0.6);
  }

  video {
    width: 100%;
    height: auto;
    display: block;
  }

  .photo-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: 1rem;
    width: 100%;
    max-width: 1200px;
  }

  .photo-grid img {
    width: 100%;
    height: 220px;
    object-fit: cover;
    border-radius: 12px;
    transition: transform 0.3s ease, box-shadow 0.3s ease;
    box-shadow: 0 0 15px rgba(255, 110, 196, 0.3);
    cursor: pointer;
  }

  .photo-grid img:hover {
    transform: scale(1.05);
    box-shadow: 0 0 25px rgba(0, 198, 255, 0.6);
  }

  /* Lightbox */
  .lightbox {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.9);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 1000;
  }

  .lightbox img {
    max-width: 90%;
    max-height: 90%;
    border-radius: 10px;
    box-shadow: 0 0 30px rgba(255, 110, 196, 0.6);
  }

  .lightbox-close {
    position: absolute;
    top: 20px;
    right: 30px;
    font-size: 2rem;
    color: white;
    cursor: pointer;
    font-family: sans-serif;
  }

  @media (max-width: 768px) {
    h1 {
      font-size: 2.2rem;
    }
    .photo-grid {
      gap: 0.7rem;
    }
    .photo-grid img {
      height: 180px;
    }
  }

  @media (max-width: 480px) {
    h1 {
      font-size: 1.8rem;
    }
    .photo-grid img {
      height: 150px;
    }
  }
</style>

<div class="gallery-container">
  <h1>Gallery & Highlights</h1>

  <!-- Main video -->
  <div class="video-highlight">
    <video 
      src={videoUrl} 
      controls 
      preload="metadata"
      poster="/logo.png"
    >
      Your browser does not support the video tag.
    </video>
  </div>

  <!-- Photos -->
  <div class="photo-grid">
    {#each photos as photo}
      <img src={photo} alt="Event photo" loading="lazy" on:click={() => selectedPhoto = photo} />
    {/each}
  </div>
</div>

<!-- Lightbox modal -->
{#if selectedPhoto}
  <div class="lightbox" on:click={() => selectedPhoto = null}>
    <span class="lightbox-close">&times;</span>
    <img src={selectedPhoto} alt="Big view" />
  </div>
{/if}
