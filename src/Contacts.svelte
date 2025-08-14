<script>
  let email = "eureka2025@example.com"; // Replace with actual email
</script>

<style>
  .contacts-container {
    max-width: 1000px;
    margin: auto;
    color: white;
    font-family: Arial, sans-serif;
    text-align: center;
  }

  h1 {
    font-size: 3rem;
    margin-bottom: 2rem;
    font-family: 'Transcity DEMO', sans-serif;
  }

  .contacts-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2rem;
    margin-bottom: 2rem;
  }

  .contacts-grid div {
    text-align: center;
  }

  h2 {
    font-size: 1.2rem;
    margin-bottom: 0.5rem;
    text-transform: uppercase;
  }

  p {
    margin: 0.3rem 0;
  }

  .social-links {
    margin-top: 1.5rem;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0.8rem;
  }

  .social-item {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    text-decoration: none;
    color: white;
    font-size: 1rem;
    transition: transform 0.3s ease, box-shadow 0.3s ease;
  }

  /* Hover animation: grow slightly */
  .social-item:hover {
    transform: scale(1.08);
  }

  /* Make sure the icon grows with the text */
  .social-item img {
    transition: transform 0.3s ease;
  }

  .social-item:hover img {
    transform: scale(1.15);
  }

  @media (max-width: 768px) {
    .contacts-grid {
      grid-template-columns: 1fr;
    }
  }
</style>

<div class="contacts-container">
  <h1>CONTACT DETAILS</h1>

  <div class="contacts-grid">
    <div>
      <h2>Faculty Coordinators</h2>
      <p>Dr Basudeb Sain</p>
      <p>Dr Levna Chacko</p>
      <p>Dr Partha Kumbhakar</p>
    </div>

    <div>
      <h2>Student Coordinators</h2>
      <p>Ekjot Kaur</p>
      <p>Akshatha Nagari</p>
    </div>

    <div>
      <h2>Contact Numbers</h2>
      <p>+91 9417537663</p>
      <p>+91 7899341168</p>
      <p>+91 7490007305</p>
    </div>
  </div>

  <div class="social-links">
    <a class="social-item" href="https://instagram.com/eureka_2025.pa" target="_blank">
      <img src="/instagram.png" alt="Instagram" width="24" height="24" />
      @eureka_2025.pa
    </a>

    <a class="social-item" href="https://www.linkedin.com/company/department-of-physics-electronics-christ-university" target="_blank">
      <img src="/linkedin.png" alt="LinkedIn" width="24" height="24" />
      Department of Physics & Electronics, Christ University
    </a>

    <!--<a class="social-item" href="mailto:{email}">
      <img src="/email.png" alt="Email" width="24" height="24" />
      {email}
    </a> -->
  </div>
</div>
