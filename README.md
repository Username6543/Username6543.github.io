<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>3D Printing On Demand</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap');

    html {
      scroll-behavior: smooth;
      background: #e9f0f8;
      font-family: 'Poppins', sans-serif;
      color: #222;
    }

    body {
      margin: 0;
      display: flex;
      flex-direction: column;
      min-height: 100vh;
    }

    nav {
      position: sticky;
      top: 0;
      background: #cc5500;
      display: flex;
      justify-content: center;
      gap: 2.5rem;
      padding: 1rem 0;
      z-index: 100;
      box-shadow: 0 3px 12px rgba(204, 85, 0, 0.6);
      user-select: none;
    }

    nav a {
      color: white;
      font-weight: 600;
      text-decoration: none;
      font-size: 1.05rem;
      text-transform: uppercase;
      padding: 0.4rem 0.6rem;
      border-radius: 8px;
      transition: background-color 0.3s ease, color 0.3s ease;
    }

    nav a:hover,
    nav a:focus {
      background: #a24400;
      outline: none;
      color: #ffe6cc;
    }

    header {
      background: #cc5500;
      color: white;
      padding: 2rem 2rem 1.5rem;
      text-align: center;
      box-shadow: 0 3px 10px rgba(204, 85, 0, 0.5);
      user-select: none;
      position: relative;
    }

    header h1 {
      margin: 0;
      font-weight: 700;
      font-size: 2.75rem;
      letter-spacing: 2px;
      text-transform: uppercase;
    }

    header p {
      margin-top: 0.4rem;
      font-weight: 400;
      font-size: 1.25rem;
      letter-spacing: 0.5px;
      line-height: 1.3;
    }

    #topOrderButton {
      margin: 1.5rem auto 3rem;
      display: block;
      background: #cc5500;
      color: white;
      font-weight: 600;
      font-size: 1.3rem;
      padding: 0.95rem 3rem;
      border: none;
      border-radius: 60px;
      cursor: pointer;
      box-shadow: 0 9px 20px rgba(204, 85, 0, 0.5);
      user-select: none;
      max-width: 320px;
      transition: background-color 0.25s ease;
    }

    #topOrderButton:hover {
      background: #a24400;
      box-shadow: 0 13px 26px rgba(162, 68, 0, 0.7);
    }

    main {
      flex: 1;
      max-width: 900px;
      margin: 0 auto 4rem;
      padding: 0 1rem;
      width: 100%;
      min-height: 500px;
    }

    section {
      margin-bottom: 3rem;
    }

    .intro {
      text-align: center;
      color: #2b3e50;
      margin-bottom: 3rem;
    }

    .intro h2 {
      font-weight: 600;
      font-size: 2.4rem;
      margin-bottom: 0.7rem;
    }

    .intro p {
      font-weight: 400;
      font-size: 1.15rem;
      max-width: 650px;
      margin: 0 auto;
      line-height: 1.6;
      color: #444;
      user-select: text;
    }

    .services {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 2.5rem;
      margin-bottom: 3rem;
    }

    .service-card {
      background: white;
      border-radius: 14px;
      box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
      flex: 1 1 280px;
      max-width: 320px;
      padding: 2rem 2.5rem;
      transition: transform 0.3s ease, box-shadow 0.3s ease;
      cursor: default;
      text-align: center;
      user-select: none;
      font-weight: 400;
      color: #333;
    }

    .service-card:hover {
      transform: translateY(-9px);
      box-shadow: 0 16px 35px rgba(0, 0, 0, 0.15);
    }

    .service-icon {
      font-size: 3.8rem;
      color: #cc5500;
      margin-bottom: 1.3rem;
      user-select: none;
    }

    .service-title {
      font-weight: 600;
      font-size: 1.4rem;
      color: #223344;
      margin-bottom: 1rem;
      user-select: text;
    }

    .service-description {
      font-weight: 400;
      font-size: 1rem;
      line-height: 1.6;
      color: #555;
      user-select: text;
    }

    #about h2,
    #contact h2,
    #order h2 {
      text-align: center;
      font-weight: 600;
      font-size: 2.2rem;
      margin-bottom: 1rem;
      color: #223344;
      user-select: text;
    }

    #about p,
    #order p {
      font-weight: 400;
      font-size: 1.15rem;
      max-width: 700px;
      margin: 0 auto 1.5rem;
      line-height: 1.7;
      color: #444;
      user-select: text;
    }

    #contact form,
    #order form {
      max-width: 550px;
      margin: 0 auto;
      background: white;
      padding: 2.5rem 3rem;
      border-radius: 14px;
      box-shadow: 0 12px 30px rgba(0, 0, 0, 0.1);
      user-select: none;
      font-size: 1rem;
      color: #222;
    }

    #contact label,
    #order label {
      display: block;
      margin-bottom: 0.45rem;
      font-weight: 600;
      color: #333;
      user-select: text;
      text-align: left;
    }

    #contact input[type="text"],
    #contact input[type="email"],
    #contact textarea,
    #order input[type="email"],
    #order select {
      width: 100%;
      padding: 0.7rem 0.85rem;
      margin-bottom: 1.5rem;
      border: 2px solid #ddd;
      border-radius: 8px;
      font-family: 'Poppins', sans-serif;
      font-weight: 400;
      font-size: 1rem;
      transition: border-color 0.3s ease;
      resize: vertical;
      box-sizing: border-box;
      color: #222;
      user-select: text;
    }

    #contact input[type="text"]:focus,
    #contact input[type="email"]:focus,
    #contact textarea:focus,
    #order input[type="email"]:focus,
    #order select:focus {
      outline: none;
      border-color: #cc5500;
    }

    #contact textarea {
      min-height: 120px;
    }

    #order p.instructions {
      font-weight: 400;
      color: #555;
      max-width: 400px;
      margin: 0 auto 2rem;
      font-size: 0.95rem;
    }

    #order .back-btn {
      background: transparent;
      color: #cc5500;
      border: none;
      font-weight: 600;
      font-size: 1rem;
      text-decoration: underline;
      margin-top: 1.5rem;
      cursor: pointer;
      user-select: none;
      display: block;
      margin-left: auto;
      margin-right: auto;
    }

    #order .back-btn:hover {
      color: #a24400;
    }

    #uploadName {
      margin-top: 0;
      font-style: italic;
      color: #555;
      min-height: 1.2rem;
      user-select: text;
      word-break: break-word;
    }

    #order button[type="submit"],
    #contact button[type="submit"] {
      background: #cc5500;
      color: white;
      font-weight: 600;
      font-size: 1.15rem;
      padding: 0.9rem 2.5rem;
      border: none;
      border-radius: 50px;
      cursor: pointer;
      transition: background-color 0.3s ease;
      box-shadow: 0 10px 25px rgba(204, 85, 0, 0.5);
      user-select: none;
      display: block;
      width: 100%;
      margin-top: 0.5rem;
    }

    #order button[type="submit"]:hover,
    #contact button[type="submit"]:hover {
      background: #a24400;
      box-shadow: 0 14px 28px rgba(162, 68, 0, 0.7);
    }

    footer {
      background: #613500;
      color: #f0e6dc;
      text-align: center;
      padding: 1rem 1rem;
      font-weight: 300;
      font-size: 0.9rem;
      user-select: none;
    }

    /* Responsive rules */
    @media (max-width: 730px) {
      main {
        margin: 2rem 1rem 3rem;
      }
      .services {
        flex-direction: column;
        align-items: center;
      }
      #order form,
      #contact form {
        width: 100%;
        padding: 1.5rem 1.75rem;
      }
      #topOrderButton {
        margin: 1rem auto 2rem;
        width: 90%;
        max-width: 320px;
      }
    }
  </style>
</head>
<body>
  <nav aria-label="Primary navigation">
    <a href="#home" tabindex="0" class="nav-link" data-target="homeSection">Home</a>
    <a href="#about" tabindex="0" class="nav-link" data-target="aboutSection">About</a>
    <a href="#services" tabindex="0" class="nav-link" data-target="servicesSection">Services</a>
    <a href="#contact" tabindex="0" class="nav-link" data-target="contactSection">Contact</a>
  </nav>
  <header id="homeSection">
    <h1>3D Printing On Demand</h1>
    <p>Fast, Precise, And Custom 3D Printing Solutions Whenever You Need</p>
  </header>

  <!-- Order button placed at top -->
  <button id="topOrderButton" aria-label="Order Your 3D Print">Order Your 3D Print</button>

  <main>
    <!-- Main content section -->
    <section id="mainPage">
      <section class="intro" id="aboutSection">
        <h2>About Us</h2>
        <p>
          At 3D Printing On Demand, we are passionate about bringing your ideas to life with the latest 3D printing technology. Founded by experts in additive manufacturing, we provide reliable, fast, and precise 3D printing services to individuals and businesses alike. Our mission is to make professional 3D printing accessible and affordable, helping you prototype, produce, and innovate with confidence.
        </p>
      </section>
      <section class="services" aria-label="Our 3D Printing Service Features" id="servicesSection">
        <article class="service-card">
          <div class="service-icon" aria-hidden="true">⚡</div>
          <h3 class="service-title">Rapid Turnaround</h3>
          <p class="service-description">Get your 3D printed parts delivered fast with our streamlined printing and shipping process.</p>
        </article>
        <article class="service-card">
          <div class="service-icon" aria-hidden="true">🎨</div>
          <h3 class="service-title">High Precision</h3>
          <p class="service-description">We use advanced printers to ensure every print matches your design exactly, down to the finest detail.</p>
        </article>
        <article class="service-card">
          <div class="service-icon" aria-hidden="true">🌍</div>
          <h3 class="service-title">Wide Material Choice</h3>
          <p class="service-description">Choose from a variety of materials including PLA, PLA+, TPU, ABS, and PETG to suit your project needs.</p>
        </article>
        <article class="service-card">
          <div class="service-icon" aria-hidden="true">💻</div>
          <h3 class="service-title">Easy Online Upload</h3>
          <p class="service-description">Upload your 3D models securely and get instant pricing and order tracking all through our website.</p>
        </article>
      </section>
      <section id="contactSection" aria-label="Contact section">
        <h2>Contact Us</h2>
        <form id="contactForm" novalidate>
          <label for="name">Name<span aria-hidden="true">*</span></label>
          <input type="text" id="name" name="name" placeholder="Your full name" required minlength="2" autocomplete="name" />

          <label for="email">Email<span aria-hidden="true">*</span></label>
          <input type="email" id="email" name="email" placeholder="Your email address" required autocomplete="email" />

          <label for="message">Message<span aria-hidden="true">*</span></label>
          <textarea id="message" name="message" placeholder="Write your message here" required minlength="10"></textarea>

          <button type="submit">Send Message</button>
        </form>
      </section>
    </section>

    <!-- Order page section -->
    <section id="orderPage" style="display:none;">
      <h2>Order Your 3D Print</h2>
      <p class="instructions">
        To place an order, please fill out your email and select the options below.
        You will then be redirected to our secure Google Form to complete your upload and finalize the order.
      </p>
      <form id="orderForm" novalidate>
        <label for="emailOrder">Your Email<span aria-hidden="true">*</span></label>
        <input type="email" id="emailOrder" name="emailOrder" placeholder="you@example.com" required autocomplete="email" />

        <label for="colorSelect">Choose Color<span aria-hidden="true">*</span></label>
        <select id="colorSelect" name="colorSelect" required>
          <option value="" disabled selected>Select a color</option>
          <option value="White">White</option>
          <option value="Grey">Grey</option>
          <option value="Purple">Purple</option>
          <option value="Orange">Orange</option>
          <option value="Blue">Blue</option>
          <option value="Black">Black</option>
        </select>

        <label for="materialSelect">Choose Material<span aria-hidden="true">*</span></label>
        <select id="materialSelect" name="materialSelect" required>
          <option value="" disabled selected>Select a material</option>
          <option value="PLA">PLA</option>
          <option value="PLA+">PLA+</option>
          <option value="TPU">TPU</option>
          <option value="ABS">ABS</option>
          <option value="PETG">PETG</option>
        </select>

        <label for="quantitySelect">Number of Prints<span aria-hidden="true">*</span></label>
        <select id="quantitySelect" name="quantitySelect" required>
          <option value="" disabled selected>Select quantity</option>
          <option value="1">1</option>
          <option value="2">2</option>
          <option value="3">3</option>
          <option value="4">4</option>
          <option value="5">5</option>
          <option value="6">6</option>
          <option value="7">7</option>
          <option value="8">8</option>
          <option value="9">9</option>
          <option value="10">10</option>
        </select>

        <button type="submit">Continue to Upload Form</button>
      </form>
      <button class="back-btn" id="backToMain">← Back to Home</button>
    </section>
  </main>
  <footer>
    &copy; 2024 3D Printing On Demand — All Rights Reserved
  </footer>

  <script>
    // Navigation links scroll to sections on main page only
    document.querySelectorAll('nav a.nav-link').forEach(link => {
      link.addEventListener('click', e => {
        e.preventDefault();
        if (document.getElementById('orderPage').style.display !== 'none') {
          goToMainPage(() => scrollToSection(link.dataset.target));
        } else {
          scrollToSection(link.dataset.target);
        }
      });
    });

    function scrollToSection(id) {
      const section = document.getElementById(id);
      if (section) section.scrollIntoView({ behavior: 'smooth' });
    }

    const orderButtonTop = document.getElementById('topOrderButton');
    const orderPage = document.getElementById('orderPage');
    const mainPage = document.getElementById('mainPage');
    const backToMainButton = document.getElementById('backToMain');

    // Show order page function
    function goToOrderPage() {
      mainPage.style.display = 'none';
      orderPage.style.display = 'block';
      window.scrollTo({ top: 0, behavior: 'smooth' });

      // Reset form values
      document.getElementById('orderForm').reset();
    }

    // Show main page function with optional callback
    function goToMainPage(callback) {
      orderPage.style.display = 'none';
      mainPage.style.display = 'block';
      window.scrollTo({ top: 0, behavior: 'smooth' });
      if (callback) callback();
    }

    orderButtonTop.addEventListener('click', () => {
      goToOrderPage();
    });

    backToMainButton.addEventListener('click', () => {
      goToMainPage();
    });

    document.getElementById('orderForm').addEventListener('submit', event => {
      event.preventDefault();

      const email = document.getElementById('emailOrder').value.trim();
      const color = document.getElementById('colorSelect').value;
      const material = document.getElementById('materialSelect').value;
      const quantity = document.getElementById('quantitySelect').value;

      // Basic validation
      if (!email || !email.includes('@')) {
        alert('Please enter a valid email address.');
        document.getElementById('emailOrder').focus();
        return;
      }
      if (!color) {
        alert('Please select a color.');
        document.getElementById('colorSelect').focus();
        return;
      }
      if (!material) {
        alert('Please select a material.');
        document.getElementById('materialSelect').focus();
        return;
      }
      if (!quantity) {
        alert('Please select the number of prints.');
        document.getElementById('quantitySelect').focus();
        return;
      }

      // Prefill Google Form URL parameters based on your form's input field IDs
      // Note: Replace the entry.xxxxxxx values with your actual Google Form field IDs
      // You must find these IDs by inspecting your Google Form's page source or URL when pre-filling
      
      const baseGoogleFormUrl = 'https://docs.google.com/forms/d/e/1FAIpQLSeaRt-NV2IrsSnOC9j-lHSBdywclbp2PpCPFoUOopA7tlaiTQ/viewform?usp=pp_url';

      // Example Google Form field entry ids (you must replace these with your actual form field names)
      const params = new URLSearchParams();
      // Let's assume:
      // Email field entry: entry.1234567890
      // Color field entry: entry.2345678901
      // Material field entry: entry.3456789012
      // Quantity field entry: entry.4567890123

      // IMPORTANT! Replace below with your actual Google Form URL parameter keys.
      params.append('entry.1234567890', email);
      params.append('entry.2345678901', color);
      params.append('entry.3456789012', material);
      params.append('entry.4567890123', quantity);

      const fullUrl = `${baseGoogleFormUrl}&${params.toString()}`;

      // Inform user about redirect and upload part on Google Form
      alert('You will now be redirected to our secured Google Form to complete your upload and order details.');

      window.open(fullUrl, '_blank');

      // Return to main page
      goToMainPage();
    });

    // Contact form submission (unchanged)
    document.getElementById('contactForm').addEventListener('submit', function(event) {
      event.preventDefault();

      const name = this.name.value.trim();
      const email = this.email.value.trim();
      const message = this.message.value.trim();

      if (name.length < 2) {
        alert('Please enter a valid name with at least 2 characters.');
        this.name.focus();
        return;
      }
      if (!email || !email.includes('@')) {
        alert('Please enter a valid email address.');
        this.email.focus();
        return;
      }
      if (message.length < 10) {
        alert('Please enter a message with at least 10 characters.');
        this.message.focus();
        return;
      }

      alert('Thank you for contacting us, ' + name + '! We will get back to you shortly.');
      this.reset();
    });
  </script>
</body>
</html>

