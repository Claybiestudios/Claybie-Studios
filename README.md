<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Claybie Mug Customizer</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background-color: #f5f3e7;
      color: #550000;
      margin: 0;
      padding: 20px;
    }
    .page {
      display: none;
    }
    .active {
      display: block;
    }
    button, input[type="submit"] {
      background-color: #550000;
      color: white;
      padding: 10px 20px;
      border: none;
      cursor: pointer;
      border-radius: 8px;
    }
    h1, h2 {
      color: #550000;
    }
    .form-group {
      margin-bottom: 20px;
    }
    .total {
      font-weight: bold;
    }
  </style>
</head>
<body><div id="page1" class="page active">
  <h1>Welcome to Claybie</h1>
  <p>At Claybie, your mug becomes your world ✨<br>
    We turn cozy cups into magical moments—with Ghibli-style portraits 🌸, anime character vibes 🎌, and even designs inspired by your fave K-pop idol 🎤.<br>
    Everything’s handmade, personalized, and totally aesthetic ☁️.<br>
    So if you’ve ever dreamed of sipping from a cup that looks like it walked out of a Studio Ghibli scene or your favourite idols' MV—welcome home.</p>
  <button onclick="nextPage(2)">Start Customizing</button>
</div><div id="page2" class="page">
  <h2>Customize Your Mug</h2>
  <form id="customForm">
    <div class="form-group">
      <label>Want portrait on your mug?</label><br>
      <input type="radio" name="portrait" value="11.63" required onchange="togglePortraitUpload(true)"> 1 portrait (+$11.63)<br>
      <input type="radio" name="portrait" value="21.01" onchange="togglePortraitUpload(true)"> 2 portrait (+$21.01)<br>
    </div>
    <div id="portraitUpload" class="form-group" style="display: none;">
      <label>Upload your portrait</label>
      <input type="file" required id="portraitFile">
    </div>
    <div class="form-group">
      <label>Pick your cute 3D decorations (outside of the mug, small)</label><br>
      <select name="small3D" required onchange="updatePrice(this)">
        <option value="0">None</option>
        <option value="5.83">Small bow 🎀</option>
        <option value="9.34">3 medium bows 🎀</option>
        <option value="3.50">Heart ❤️</option>
        <option value="8.17">Cherry 🍒</option>
        <option value="7.01">Strawberry 🍓</option>
        <option value="11.68">Cat footprint 🐾</option>
        <option value="11.68">Dog footprint 🐾</option>
        <option value="9.34">Teddy bear 🧸</option>
        <option value="7.01">Butterfly 🦋</option>
      </select>
    </div>
    <!-- Repeat structure for all other questions as above -->
    <div class="form-group">
      <label>Wanna add text to your mug?</label><br>
      <input type="radio" name="textAdd" value="5.84" required onchange="toggleTextInput(true)"> Inside (+$5.84)<br>
      <input type="radio" name="textAdd" value="8.17" onchange="toggleTextInput(true)"> Outside (+$8.17)<br>
      <input type="radio" name="textAdd" value="11.68" onchange="toggleTextInput(true)"> Both (+$11.68)<br>
    </div>
    <div id="textInput" class="form-group" style="display: none;">
      <label>Write your text below</label>
      <textarea id="customText" required></textarea>
    </div>
    <p class="total">Total: $<span id="totalPrice">46.69</span></p>
    <button type="button" onclick="nextPage(3)">Proceed to Buy</button>
  </form>
</div><div id="page3" class="page">
  <h2>Shipping Info</h2>
  <form id="shippingForm">
    <div class="form-group">
      <label>Full Name:</label>
      <input type="text" required>
    </div>
    <div class="form-group">
      <label>Contact Number:</label>
      <input type="tel" required>
    </div>
    <div class="form-group">
      <label>Email:</label>
      <input type="email" required>
    </div>
    <div class="form-group">
      <label>Shipping Address:</label>
      <textarea required></textarea>
    </div>
    <button type="button" onclick="nextPage(4)">Proceed to Payment</button>
  </form>
</div><div id="page4" class="page">
  <h2>Payment</h2>
  <p>Choose your payment method:</p>
  <ul>
    <li><strong>Google Pay:</strong> 6352177416@ptaxis</li>
    <li><strong>PayPal:</strong> <a href="https://www.paypal.me/KavitaVarma883" target="_blank">paypal.me/KavitaVarma883</a></li>
  </ul>
  <p><strong>Note:</strong> Please complete your payment and then click below.</p>
  <button onclick="nextPage(5)">I’ve Paid</button>
</div><div id="page5" class="page">
  <h2>Thanks for ordering!</h2>
  <p>Your order is confirmed. We’ll start working on your magical mug right away!</p>
</div><script>
  const basePrice = 46.69;
  let currentTotal = basePrice;

  function nextPage(pageNumber) {
    document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
    document.getElementById('page' + pageNumber).classList.add('active');
  }

  function updatePrice(selectEl) {
    const options = document.querySelectorAll('select, input[type=radio]:checked');
    let newTotal = basePrice;
    options.forEach(opt => {
      if (opt.value) newTotal += parseFloat(opt.value);
    });
    document.getElementById('totalPrice').innerText = newTotal.toFixed(2);
  }

  function togglePortraitUpload(show) {
    document.getElementById('portraitUpload').style.display = show ? 'block' : 'none';
    if (show) document.getElementById('portraitFile').required = true;
    updatePrice();
  }

  function toggleTextInput(show) {
    document.getElementById('textInput').style.display = show ? 'block' : 'none';
    if (show) document.getElementById('customText').required = true;
    updatePrice();
  }

  document.querySelectorAll('input[type=radio], select').forEach(el => {
    el.addEventListener('change', updatePrice);
  });
</script></body>
</html>
