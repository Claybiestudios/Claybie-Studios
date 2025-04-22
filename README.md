<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Claybie Mug Customizer</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background-color: #f5f1e6;
      color: #4a1c1a;
      margin: 0;
      padding: 0;
    }
    header, section, footer {
      padding: 20px;
      max-width: 800px;
      margin: auto;
    }
    h1, h2, h3, label {
      color: #7b1e1e;
    }
    .button {
      background-color: #7b1e1e;
      color: white;
      border: none;
      padding: 10px 20px;
      margin-top: 20px;
      cursor: pointer;
    }
    .button:hover {
      background-color: #5e1515;
    }
    input, select, textarea {
      width: 100%;
      padding: 10px;
      margin: 10px 0;
      border: 1px solid #ccc;
      border-radius: 4px;
    }
    .hidden { display: none; }
  </style>
</head>
<body>
<!-- Page 1 -->
<section id="page1">
  <h1>Welcome to Claybie!</h1>
  <p>
    At Claybie, your mug becomes your world ✨<br>
    We turn cozy cups into magical moments—with Ghibli-style portraits 🌸,
    anime character vibes 🎌, and even designs inspired by your fave K-pop idol 🎤.<br>
    Everything’s handmade, personalized, and totally aesthetic ☁️.<br>
    So if you’ve ever dreamed of sipping from a cup that looks like it walked out of a Studio Ghibli scene or your favourite idols' MV—welcome home.
  </p>
  <button class="button" onclick="nextPage('page1','page2')">Customize Your Mug</button>
</section>

<!-- Page 2 - Customization Form -->
<section id="page2" class="hidden">
  <h2>Mug Customization</h2>
  <form id="customForm">
    <input type="hidden" id="basePrice" value="46.69">

    <!-- All your customization questions here (already included in your original code) -->

    <!-- Question 1 -->
    <label>Want portrait on your mug?</label>
    <select id="portrait" name="portrait" required onchange="handlePortrait(this.value)">
      <option value="">--Select--</option>
      <option value="1" data-price="11.63">1 portrait – $11.63</option>
      <option value="2" data-price="21.01">2 portraits – $21.01</option>
      <option value="none" data-price="0">No portrait – $0</option>
    </select>
    <div id="portraitUpload" class="hidden">
      <label>Upload your portrait</label>
      <input type="file" name="portraitFile" id="portraitFile" accept="image/*">
    </div>

    <!-- All your other select questions remain the same (with price tags shown as part of options) -->

    <!-- Question 2 to 6 (same as your full code above) -->

    <!-- Text input conditionally shown -->
    <div id="textInput" class="hidden">
      <label>Write your text below</label>
      <textarea name="customText" id="customText" required></textarea>
    </div>

    <h3>Total Price: $<span id="totalPrice">46.69</span></h3>
    <button type="button" class="button" onclick="nextPage('page2','page3')">Next</button>
  </form>
</section>

<!-- Page 3 - Contact Info -->
<section id="page3" class="hidden">
  <h2>Your Details</h2>
  <form id="infoForm" onsubmit="event.preventDefault(); nextPage('page3','page4');">
    <label>Full Name</label>
    <input type="text" name="fullName" required>
    <label>Contact Number</label>
    <input type="tel" name="contactNumber" required>
    <label>Email</label>
    <input type="email" name="email" required>
    <label>Shipping Address</label>
    <textarea name="address" required></textarea>
    <button type="submit" class="button">Proceed to Payment</button>
  </form>
</section>

<!-- Page 4 - Payment -->
<section id="page4" class="hidden">
  <h2>Payment</h2>
  <p>Choose a payment method:</p>
  <p><strong>Google Pay:</strong> 6352177416@ptaxis</p>
  <p><strong>PayPal:</strong> <a href="https://www.paypal.me/KavitaVarma883" target="_blank">paypal.me/KavitaVarma883</a></p>
  <p>Once payment is done, click below to confirm:</p>
  <button class="button" onclick="nextPage('page4','page5')">Confirm Payment</button>
</section>

<!-- Page 5 - Confirmation -->
<section id="page5" class="hidden">
  <h2>Thank you for ordering!</h2>
  <p>Your order is confirmed. You’re the best!</p>
</section>

<script>
function nextPage(current, next) {
  document.getElementById(current).classList.add('hidden');
  document.getElementById(next).classList.remove('hidden');
  updatePrice();
}

function handlePortrait(value) {
  const portraitUpload = document.getElementById('portraitUpload');
  if (value === '1' || value === '2') {
    portraitUpload.classList.remove('hidden');
    document.getElementById('portraitFile').setAttribute('required', true);
  } else {
    portraitUpload.classList.add('hidden');
    document.getElementById('portraitFile').removeAttribute('required');
  }
  updatePrice();
}

function handleText(value) {
  const textBox = document.getElementById('textInput');
  if (value === 'inside' || value === 'outside' || value === 'both') {
    textBox.classList.remove('hidden');
    document.getElementById('customText').setAttribute('required', true);
  } else {
    textBox.classList.add('hidden');
    document.getElementById('customText').removeAttribute('required');
  }
  updatePrice();
}

function updatePrice() {
  let total = parseFloat(document.getElementById('basePrice').value);
  const selects = document.querySelectorAll('#customForm select');
  selects.forEach(sel => {
    const selected = sel.options[sel.selectedIndex];
    const price = parseFloat(selected.dataset.price || 0);
    total += price;
  });
  document.getElementById('totalPrice').innerText = total.toFixed(2);
}
</script>
</body>
</html>