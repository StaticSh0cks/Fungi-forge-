<!<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Fungi Forge</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link href="https://fonts.googleapis.com/css2?family=Inter&display=swap" rel="stylesheet">

  <style>
    html {
      scroll-behavior: smooth;
    }

    body {
      font-family: 'Inter', sans-serif;
      background-color: black;
      color: white;
      margin: 0;
      padding: 0;
      line-height: 1.6;
    }

    .overlay {
      padding: 2rem;
      min-height: 100vh;
    }

    header {
      background-color: #2d5731;
      padding: 1rem;
      text-align: center;
      color: white;
      border-radius: 12px;
    }

    h2 {
      font-size: 2rem;
    }

    .accordion {
      max-width: 800px;
      margin: 2rem auto;
      background-color: #444;
      border-radius: 10px;
      overflow: hidden;
    }

    .accordion-item {
      border-top: 1px solid #555;
    }

    .accordion-item:first-child {
      border-top: none;
    }

    .accordion-header {
      background-color: #2d5731;
      padding: 1rem;
      color: white;
      font-size: 1.2rem;
      cursor: pointer;
      text-align: center;
      transition: background-color 0.3s;
    }

    .accordion-header:hover {
      background-color: #3a7c42;
    }

    .accordion-content {
      display: none;
      padding: 1rem;
      background-color: rgba(255, 255, 255, 0.1);
      color: white;
      transition: max-height 0.3s ease, opacity 0.3s ease;
    }

    .accordion-content ul {
      list-style-type: none;
      padding-left: 1.2rem;
    }

    .accordion-content li {
      margin-bottom: 0.5rem;
    }

    .accordion-content a, .accordion-content button {
      text-decoration: none;
      color: white;
      font-weight: bold;
    }

    .button {
      display: inline-block;
      margin-top: 1rem;
      padding: 0.6rem 1.2rem;
      background-color: #4CAF50;
      color: white !important;
      text-decoration: none;
      border: none;
      border-radius: 8px;
      font-weight: bold;
      transition: background-color 0.3s ease;
      cursor: pointer;
      text-align: center;
    }

    .button:hover {
      background-color: #3a9a3d;
    }

    footer {
      text-align: center;
      padding: 1rem;
      margin-top: 2rem;
      background-color: #2d5731;
      border-radius: 12px;
    }

    input[type="radio"] {
      accent-color: black;
    }

    .open {
      display: block !important;
    }

    /* Thank You Screen */
    #thank-you-screen {
      position: fixed;
      top: 0;
      left: 0;
      height: 100%;
      width: 100%;
      background-color: black;
      color: white;
      display: none;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      text-align: center;
      z-index: 1000;
      transition: opacity 0.5s ease;
    }

    #thank-you-screen.show {
      display: flex;
    }

    #thank-you-screen h1 {
      font-size: 2.5rem;
      margin-bottom: 1rem;
    }

    #thank-you-screen p {
      font-size: 1.2rem;
      margin-top: 3rem;
      color: #aaa;
    }
  </style>
</head>

<body>
  <div class="overlay">
    <header>
      <h2>Fungi Forge</h2>
      <p>Your eco-friendly solution for recycling clothes into sustainable packaging</p>
    </header>

    <div class="accordion">
      <!-- Donate Section -->
      <div class="accordion-item">
        <div class="accordion-header">Donate to the Fungi Forge</div>
        <div class="accordion-content">
          <p>Turn your old clothes into eco-packaging while making a profit. <strong>The Fungi Forge</strong> uses mycelium to break down synthetic and natural materials like nylon, cotton, and polyester — and transform them into sustainable packaging.</p>
          <ul>
            <li>We accept clean cotton, denim, polyester, or nylon clothing.</li>
            <li>Your donation helps grow zero-waste packaging.</li>
            <li>Powered by innovation.</li>
          </ul>
          <a href="#plastic-section" class="button">Donate Clothes →</a>
        </div>
      </div>

      <!-- Plastic Type Section -->
      <div class="accordion-item" id="plastic-section">
        <div class="accordion-header">Select Plastic Type</div>
        <div class="accordion-content">
          <p>Please choose the type of plastic you are donating:</p>
          <form id="plastic-form">
            <label><input type="radio" name="plastic" value="nylon"> Nylon</label><br>
            <label><input type="radio" name="plastic" value="polythene"> Polythene</label><br>
            <label><input type="radio" name="plastic" value="polyester"> Polyester</label><br><br>
            <button type="submit" class="button">Submit Donation</button>
          </form>
        </div>
      </div>

      <!-- Customer Service Section -->
      <div class="accordion-item">
        <div class="accordion-header">Customer Service</div>
        <div class="accordion-content">
          <p>If you have any questions or need assistance, don't hesitate to contact us!</p>
          <a href="mailto:info@fungiforge.com" class="button">Email Us</a>
        </div>
      </div>

      <!-- Useful Links Section -->
      <div class="accordion-item">
        <div class="accordion-header">Go Back to Home Page</div>
        <div class="accordion-content">
          <p>Discover more about our initiatives and projects by visiting the links below:</p>
          <a href="your-link-here" class="button">Learn More</a>
        </div>
      </div>
    </div>

    <footer>
      <p>Fungi Forge &copy; 2025. All rights reserved.</p>
    </footer>
  </div>

  <!-- Thank You Screen -->
  <div id="thank-you-screen">
    <h1>Thank you for donating</h1>
    <p>Tiyende Green</p>
  </div>

  <script>
    const accordionHeaders = document.querySelectorAll('.accordion-header');

    accordionHeaders.forEach(header => {
      header.addEventListener('click', function () {
        const content = this.nextElementSibling;
        document.querySelectorAll('.accordion-content').forEach(c => {
          if (c !== content) c.classList.remove('open');
        });
        content.classList.toggle('open');
      });
    });

    // Auto-open plastic section if navigated via hash
    window.addEventListener('load', () => {
      if (window.location.hash === '#plastic-section') {
        document.querySelector('#plastic-section .accordion-content')?.classList.add('open');
      }
    });

    // Show thank-you screen on form submission
    const form = document.getElementById('plastic-form');
    const thankYouScreen = document.getElementById('thank-you-screen');

    form.addEventListener('submit', (e) => {
      e.preventDefault();
      thankYouScreen.classList.add('show');
    });
  </script>
</body>
</html>
