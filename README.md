<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Claybie Mug Customizer</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background-color: #f5f0e6;
      color: #540b0e;
      margin: 0;
      padding: 0;
    }
    header, footer {
      background-color: #8b0000;
      color: white;
      padding: 1em;
      text-align: center;
    }
    main {
      padding: 2em;
      max-width: 700px;
      margin: auto;
    }
    section {
      margin-bottom: 2em;
    }
    label, select, input, textarea {
      display: block;
      width: 100%;
      margin-top: 0.5em;
    }
    .hidden {
      display: none;
    }
    button {
      background-color: #8b0000;
      color: white;
      border: none;
      padding: 1em;
      font-size: 1em;
      border-radius: 5px;
      cursor: pointer;
    }
    h1, h2 {
      color: #8b0000;
    }
    .price-display {
      font-weight: bold;
      font-size: 1.2em;
      margin: 1em 0;
    }
  </style>
</head>
<body>
  <header>
    <h1>Claybie Custom Mugs</h1>
  </header>  <main id="page1">
    <section>
      <h2>Welcome to Claybie</h2>
      <p>At Claybie, your mug becomes your world ✨ We turn cozy cups into magical moments—with Ghibli-style portraits 🌸, anime character vibes 🎌, and even designs inspired by your fave K-pop idol 🎤. Everything’s handmade, personalized, and totally aesthetic ☁️. So if you’ve ever dreamed of sipping from a cup that looks like it walked out of a Studio Ghibli scene or your favourite idols' MV—welcome home.</p>
    </section>
    <button onclick="showPage('page2')">Start Customizing</button>
  </main>  <main id="page2" class="hidden">
    <form id="customForm">
      <section>
        <h2>1. Want portrait on your mug?</h2>
        <select name="portrait" required onchange="handlePortraitUpload(this.value)">
          <option value="">--Select--</option>
          <option value="1portrait" data-price="11.63">1 portrait (+$11.63)</option>
          <option value="2portrait" data-price="21.01">2 portrait (+$21.01)</option>
        </select>
        <input type="file" name="portraitUpload" id="portraitUpload" class="hidden" required />
      </section><section>
    <h2>2. Pick your cute 3D decorations (outside of the mug, small)</h2>
    <select name="decoration" required onchange="updatePrice()">
      <option value="">--Select--</option>
      <option data-price="5.83">small bow 🎀 (+$5.83)</option>
      <option data-price="9.34">3 medium size bows 🎀 (+$9.34)</option>
      <option data-price="3.5">heart ❤️ (+$3.50)</option>
      <option data-price="8.17">cherry 🍒 (+$8.17)</option>
      <option data-price="7.01">strawberry 🍓 (+$7.01)</option>
      <option data-price="11.68">cat footprint 🐾 (+$11.68)</option>
      <option data-price="11.68">dog footprint 🐾 (+$11.68)</option>
      <option data-price="9.34">teddy bear 🧸 (+$9.34)</option>
      <option data-price="7.01">butterfly 🦋 (+$7.01)</option>
    </select>
  </section>

  <!-- Repeat similar sections for questions 3 to 6 -->

  <section>
    <h2>Live Total Price:</h2>
    <div class="price-display" id="totalPrice">$46.69</div>
  </section>

  <button type="button" onclick="showPage('page3')">Proceed to Buy</button>
</form>

  </main>  <main id="page3" class="hidden">
    <form id="detailsForm">
      <section>
        <h2>Your Details</h2>
        <label>Full Name: <input type="text" name="fullName" required /></label>
        <label>Contact Number: <input type="tel" name="contact" required /></label>
        <label>Email: <input type="email" name="email" required /></label>
        <label>Shipping Address: <textarea name="address" required></textarea></label>
      </section>
      <button type="button" onclick="showPage('page4')">Next</button>
    </form>
  </main>  <main id="page4" class="hidden">
    <section>
      <h2>Make Your Payment</h2>
      <p>Google Pay UPI: <strong>6352177416@ptaxis</strong></p>
      <p>or</p>
      <a href="https://www.paypal.me/KavitaVarma883" target="_blank">Pay via PayPal</a>
      <p>After payment, click below:</p>
      <button onclick="showPage('page5')">I've Paid</button>
    </section>
  </main>  <main id="page5" class="hidden">
    <section>
      <h2>Thanks for ordering!</h2>
      <p>Your order is confirmed. We’re brewing up something cute just for you!</p>
    </section>
  </main>  <footer>
    <p>&copy; 2025 Claybie. Made with love and clay.</p>
  </footer>  <script>
    let basePrice = 46.69;
    let totalPrice = basePrice;

    function showPage(pageId) {
      document.querySelectorAll("main").forEach(m => m.classList.add("hidden"));
      document.getElementById(pageId).classList.remove("hidden");
    }

    function handlePortraitUpload(value) {
      const uploadField = document.getElementById("portraitUpload");
      if (value === "1portrait" || value === "2portrait") {
        uploadField.classList.remove("hidden");
        uploadField.required = true;
      } else {
        uploadField.classList.add("hidden");
        uploadField.required = false;
      }
      updatePrice();
    }

    function updatePrice() {
      totalPrice = basePrice;
      const selects = document.querySelectorAll("select");
      selects.forEach(select => {
        const option = select.options[select.selectedIndex];
        const price = parseFloat(option.getAttribute("data-price")) || 0;
        totalPrice += price;
      });
      document.getElementById("totalPrice").textContent = "$" + totalPrice.toFixed(2);
    }
  </script></body>
</html>
