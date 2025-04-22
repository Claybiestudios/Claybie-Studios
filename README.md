<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Claybie - Magical Mugs</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background-color: #fff5f8;
      color: #4b2e2e;
      margin: 0;
      padding: 0;
    }
    header, footer {
      background-color: #fce4ec;
      text-align: center;
      padding: 1rem;
    }
    main {
      padding: 2rem;
      max-width: 800px;
      margin: auto;
    }
    .page {
      display: none;
    }
    .active {
      display: block;
    }
    button, select, input[type="text"], input[type="tel"], input[type="email"] {
      display: block;
      width: 100%;
      margin: 1rem 0;
      padding: 0.8rem;
      font-size: 1rem;
      border: 1px solid #dba0b6;
      border-radius: 8px;
    }
    button {
      background-color: #ff69b4;
      color: white;
      border: none;
      cursor: pointer;
    }
    h1, h2 {
      color: #d6336c;
      text-align: center;
    }
  </style>
</head>
<body>
  <header>
    <h1>Claybie</h1>
  </header>
  <main>
    <!-- Page 1 -->
    <div class="page active" id="page1">
      <h2>Welcome to Claybie</h2>
      <p>
        At Claybie, your mug becomes your world ✨ We turn cozy cups into magical
        moments—with Ghibli-style portraits 🌸, anime character vibes 🎌, and even
        designs inspired by your fave K-pop idol 🎤. Everything’s handmade,
        personalized, and totally aesthetic ☁️.
      </p>
      <button onclick="goToPage(2)">Customize Your Mug</button>
    </div>

    <!-- Page 2 -->
    <div class="page" id="page2">
      <h2>Customize Your Claybie Mug</h2>
      <form id="mugForm">
        <label>Portrait?
          <select name="portrait" required onchange="updatePrice()">
            <option value="">Select</option>
            <option value="0">None</option>
            <option value="11.63">1 portrait (+$11.63)</option>
            <option value="21.01">2 portraits (+$21.01)</option>
          </select>
        </label>
        <label>Small 3D decorations:
          <select name="small3d" required onchange="updatePrice()">
            <option value="">Select</option>
            <option value="0">None</option>
            <option value="5.83">Small bow (+$5.83)</option>
            <option value="9.34">3 medium bows (+$9.34)</option>
            <option value="3.50">Heart (+$3.50)</option>
          </select>
        </label>
        <label>Big 3D elements:
          <select name="big3d" required onchange="updatePrice()">
            <option value="">Select</option>
            <option value="0">None</option>
            <option value="17.51">Giant bow (+$17.51)</option>
          </select>
        </label>
        <label>Inside 3D elements:
          <select name="inside3d" required onchange="updatePrice()">
            <option value="">Select</option>
            <option value="0">None</option>
            <option value="3.50">Bow (+$3.50)</option>
            <option value="2.34">Heart (+$2.34)</option>
          </select>
        </label>
        <label>Handle decorations:
          <select name="handle" required onchange="updatePrice()">
            <option value="">Select</option>
            <option value="0">None</option>
            <option value="7.01">Bow (+$7.01)</option>
          </select>
        </label>
        <label>Text on mug:
          <select name="text" required onchange="updatePrice()">
            <option value="">Select</option>
            <option value="0">None</option>
            <option value="5.84">Inside (+$5.84)</option>
            <option value="8.17">Outside (+$8.17)</option>
            <option value="11.68">Both (+$11.68)</option>
          </select>
        </label>
        <div>Total: $<span id="totalPrice">46.69</span></div>
        <button type="submit">Next</button>
      </form>
    </div>

    <!-- Page 3 -->
    <div class="page" id="page3">
      <h2>Shipping Info</h2>
      <form id="shippingForm">
        <input type="text" placeholder="Full Name" name="name" required />
        <input type="tel" placeholder="Contact Number" name="phone" required />
        <input type="email" placeholder="Email" name="email" required />
        <input type="text" placeholder="Shipping Address" name="address" required />
        <button type="submit">Proceed to Payment</button>
      </form>
    </div>

    <!-- Page 4 -->
    <div class="page" id="page4">
      <h2>Payment</h2>
      <p>Choose a method to pay:</p>
      <p><strong>Paytm UPI:</strong> 6352177416@paytm</p>
      <p><strong>PayPal:</strong> <a href="https://www.paypal.me/KavitaVarma883" target="_blank">paypal.me/KavitaVarma883</a></p>
    </div>
  </main>

  <footer>
    <p>Made with love by Claybie</p>
  </footer>

  <script>
    function goToPage(num) {
      document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
      document.getElementById(`page${num}`).classList.add('active');
    }

    function updatePrice() {
      let basePrice = 46.69;
      const form = document.forms['mugForm'];
      for (let element of form.elements) {
        if (element.tagName === 'SELECT' && element.value !== "") {
          basePrice += parseFloat(element.value);
        }
      }
      document.getElementById('totalPrice').innerText = basePrice.toFixed(2);
    }

    // Prevent going forward without completing the forms
    document.getElementById('mugForm').addEventListener('submit', function(e) {
      e.preventDefault();
      if (this.checkValidity()) goToPage(3);
    });

    document.getElementById('shippingForm').addEventListener('submit', function(e) {
      e.preventDefault();
      if (this.checkValidity()) goToPage(4);
    });

    window.onload = updatePrice;
  </script>
</body>
</html>
