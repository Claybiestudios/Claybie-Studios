<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Claybie Mug Customizer</title>
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background-color: #fef6f1;
      color: #5e1c1c;
      margin: 0;
      padding: 0;
    }
    header, footer {
      background-color: #c63b3b;
      color: white;
      padding: 1rem;
      text-align: center;
    }
    .container {
      padding: 1rem;
      max-width: 600px;
      margin: auto;
    }
    .question {
      margin-bottom: 1.5rem;
    }
    .question label {
      font-weight: bold;
      display: block;
      margin-bottom: 0.5rem;
    }
    input[type="text"], input[type="email"], input[type="tel"], textarea, select {
      width: 100%;
      padding: 0.5rem;
      border: 1px solid #ddd;
      border-radius: 8px;
      box-sizing: border-box;
      margin-top: 0.25rem;
    }
    button {
      background-color: #c63b3b;
      color: white;
      border: none;
      padding: 0.75rem 1.5rem;
      font-size: 1rem;
      border-radius: 8px;
      cursor: pointer;
      display: block;
      margin: 2rem auto;
    }
    .price {
      font-size: 1.25rem;
      font-weight: bold;
      text-align: center;
      margin-top: 1rem;
    }
    .hidden {
      display: none;
    }
  </style>
</head>
<body>
  <header>
    <h1>Claybie Mug Customizer</h1>
  </header>  <div class="container" id="page1">
    <p>At Claybie, your mug becomes your world ✨<br>We turn cozy cups into magical moments—with Ghibli-style portraits 🌸, anime character vibes 🎌, and even designs inspired by your fave K-pop idol 🎤.<br>Everything’s handmade, personalized, and totally aesthetic ☁️.<br>If you’ve ever dreamed of sipping from a cup that looks like it walked out of a Studio Ghibli scene or your favourite idols' MV—welcome home.</p>
    <button onclick="goToPage(2)">Customize Your Mug</button>
  </div>  <form id="customizerForm">
  <div class="container hidden" id="page2">
    <div class="question">
      <label>Want portrait on your mug?</label>
      <select name="portrait" onchange="togglePortraitUpload(this)">
        <option value="none" data-price="0">None</option>
        <option value="1" data-price="11.63">1 portrait</option>
        <option value="2" data-price="21.01">2 portraits</option>
      </select>
    </div>
    <div class="question hidden" id="portraitUpload">
      <label>Upload your portrait (required)</label>
      <input type="file" name="portraitFile">
    </div><!-- REPEAT FOR OTHER QUESTIONS -->
<!-- EXAMPLE -->
<div class="question">
  <label>Pick your cute 3D decorations</label>
  <select name="decorations" onchange="updatePrice()">
    <option value="none" data-price="0">None</option>
    <option value="bow" data-price="5.83">small bow 🎀</option>
    <option value="3bows" data-price="9.34">3 medium size bows 🎀</option>
    <option value="heart" data-price="3.50">heart ❤️</option>
    <option value="cherry" data-price="8.17">cherry 🍒</option>
    <option value="strawberry" data-price="7.01">strawberry 🍓</option>
    <option value="catfoot" data-price="11.68">cat footprint 🐾</option>
    <option value="dogfoot" data-price="11.68">dog footprint 🐾</option>
    <option value="bear" data-price="9.34">teddy bear 🧸</option>
    <option value="butterfly" data-price="7.01">butterfly 🦋</option>
  </select>
</div>

<!-- Continue all questions in same structure -->

<div class="price">Total: $<span id="totalPrice">46.69</span></div>
<button type="button" onclick="goToPage(3)">Next</button>

  </div>  <div class="container hidden" id="page3">
    <div class="question">
      <label>Full name</label>
      <input type="text" name="fullname" required>
    </div>
    <div class="question">
      <label>Contact number</label>
      <input type="tel" name="phone" required>
    </div>
    <div class="question">
      <label>Email</label>
      <input type="email" name="email" required>
    </div>
    <div class="question">
      <label>Shipping address</label>
      <textarea name="address" required></textarea>
    </div>
    <button type="button" onclick="goToPage(4)">Next</button>
  </div>  <div class="container hidden" id="page4">
    <h2>Choose Your Payment Method</h2>
    <div class="question">
      <label>PayPal</label>
      <a href="https://www.paypal.me/KavitaVarma883" target="_blank">Pay via PayPal</a>
    </div>
    <div class="question">
      <label>Paytm (scan QR or use UPI)</label>
      <p>UPI: 6352177416@ptaxis</p>
    </div>
    <button type="submit">Confirm Payment</button>
  </div>  <div class="container hidden" id="page5">
    <h2>Thanks for ordering!</h2>
    <p>Your order is confirmed.</p>
  </div>
  </form>  <footer>
    <p>Claybie &copy; 2025</p>
  </footer>  <script>
    let currentPage = 1;
    let basePrice = 46.69;

    function goToPage(num) {
      document.querySelectorAll('.container').forEach((el, index) => {
        el.classList.add('hidden');
        if (index === num - 1) el.classList.remove('hidden');
      });
      updatePrice();
    }

    function togglePortraitUpload(select) {
      const value = select.value;
      const upload = document.getElementById('portraitUpload');
      if (value === 'none') {
        upload.classList.add('hidden');
        upload.querySelector('input').required = false;
      } else {
        upload.classList.remove('hidden');
        upload.querySelector('input').required = true;
      }
      updatePrice();
    }

    function updatePrice() {
      let total = basePrice;
      document.querySelectorAll('select').forEach(select => {
        const price = parseFloat(select.selectedOptions[0].dataset.price || 0);
        total += price;
      });
      document.getElementById('totalPrice').textContent = total.toFixed(2);
    }

    document.getElementById('customizerForm').addEventListener('submit', function(e) {
      e.preventDefault();
      goToPage(5);
    });
  </script></body>
</html>
