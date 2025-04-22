<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Claybie Mug Customizer</title>
  <style>
    * {
      box-sizing: border-box;
      font-family: 'Segoe UI', sans-serif;
    }
    body {
      margin: 0;
      padding: 0;
      background-color: #fdf6f0;
      color: #4a1c1c;
    }
    .container {
      max-width: 800px;
      margin: auto;
      padding: 20px;
    }
    h1, h2, h3 {
      color: #b31334;
    }
    .question {
      margin-bottom: 30px;
    }
    .question label, .question input, .question select, .question textarea {
      display: block;
      margin-top: 10px;
    }
    .price {
      font-size: 1.2em;
      margin: 20px 0;
    }
    .btn {
      background-color: #b31334;
      color: white;
      border: none;
      padding: 10px 20px;
      font-size: 16px;
      cursor: pointer;
      border-radius: 8px;
      margin-top: 20px;
    }
    .hidden {
      display: none;
    }
  </style>
</head>
<body>
  <div class="container" id="page1">
    <h1>Welcome to Claybie</h1>
    <p>At Claybie, your mug becomes your world ✨ We turn cozy cups into magical moments—with Ghibli-style portraits 🌸, anime character vibes 🎌, and even designs inspired by your fave K-pop idol 🎤. Everything’s handmade, personalized, and totally aesthetic ☁️. So if you’ve ever dreamed of sipping from a cup that looks like it walked out of a Studio Ghibli scene or your favourite idols' MV—welcome home.</p>
    <button class="btn" onclick="goToPage(2)">Start Customizing</button>
  </div>  <form id="customForm">
    <div class="container hidden" id="page2">
      <h2>Customize Your Mug</h2><!-- Question 1 -->
  <div class="question">
    <label>Want portrait on your mug?</label>
    <select name="portrait" onchange="togglePortraitUpload(this.value)">
      <option value="none" data-price="0">None</option>
      <option value="1portrait" data-price="11.63">1 Portrait (+$11.63)</option>
      <option value="2portrait" data-price="21.01">2 Portraits (+$21.01)</option>
    </select>
    <div id="portraitUpload" class="hidden">
      <label>Upload your portrait (required if selected):</label>
      <input type="file" id="portraitFile" accept="image/*" required>
    </div>
  </div>

  <!-- Question 2 -->
  <div class="question">
    <label>Pick your cute 3D decorations (outside of the mug, small)</label>
    <select name="decorOutsideSmall" onchange="updatePrice()">
      <option value="none" data-price="0">None</option>
      <option value="smallBow" data-price="5.83">Small Bow 🎀 (+$5.83)</option>
      <option value="threeBows" data-price="9.34">3 Medium Bows 🎀 (+$9.34)</option>
      <option value="heart" data-price="3.50">Heart ❤️ (+$3.50)</option>
      <option value="cherry" data-price="8.17">Cherry 🍒 (+$8.17)</option>
      <option value="strawberry" data-price="7.01">Strawberry 🍓 (+$7.01)</option>
      <option value="catPaw" data-price="11.68">Cat Footprint 🐾 (+$11.68)</option>
      <option value="dogPaw" data-price="11.68">Dog Footprint 🐾 (+$11.68)</option>
      <option value="teddy" data-price="9.34">Teddy Bear 🧸 (+$9.34)</option>
      <option value="butterfly" data-price="7.01">Butterfly 🦋 (+$7.01)</option>
    </select>
  </div>

  <!-- Question 3 -->
  <div class="question">
    <label>Want a big 3D outside the mug?</label>
    <select name="decorBig" onchange="updatePrice()">
      <option value="none" data-price="0">None</option>
      <option value="giantBow" data-price="17.51">Giant Bow 🎀❤️ (+$17.51)</option>
    </select>
  </div>

  <!-- Question 4 -->
  <div class="question">
    <label>Add 3D elements inside the mug (base area)</label>
    <select name="insideDecor" onchange="updatePrice()">
      <option value="none" data-price="0">None</option>
      <option value="bow" data-price="3.50">Bow 🎀 (+$3.50)</option>
      <option value="heart" data-price="2.34">Heart ❤️ (+$2.34)</option>
      <option value="cherry" data-price="5.84">Cherry 🍒 (+$5.84)</option>
      <option value="strawberry" data-price="5.84">Strawberry 🍓 (+$5.84)</option>
      <option value="catPaw" data-price="3.50">Cat Footprint 🐾 (+$3.50)</option>
      <option value="dogPaw" data-price="3.50">Dog Footprint 🐾 (+$3.50)</option>
      <option value="cat" data-price="11.68">Cat 😺 (+$11.68)</option>
      <option value="dog" data-price="11.68">Dog 😺 (+$11.68)</option>
      <option value="butterfly" data-price="7.01">Butterfly 🦋 (+$7.01)</option>
    </select>
  </div>

  <!-- Question 5 -->
  <div class="question">
    <label>Decorate the handle?</label>
    <select name="handleDecor" onchange="updatePrice()">
      <option value="none" data-price="0">None</option>
      <option value="bowHandle" data-price="7.01">Bow 🎀 (+$7.01)</option>
      <option value="catHandle" data-price="9.34">Cat 😺 (+$9.34)</option>
      <option value="dogHandle" data-price="9.34">Dog 🐶 (+$9.34)</option>
    </select>
  </div>

  <!-- Question 6 -->
  <div class="question">
    <label>Wanna add text to your mug?</label>
    <select name="textAdd" onchange="toggleTextInput(this.value)">
      <option value="none" data-price="0">None</option>
      <option value="inside" data-price="5.84">Inside the mug (+$5.84)</option>
      <option value="outside" data-price="8.17">Outside the mug (+$8.17)</option>
      <option value="both" data-price="11.68">Both (+$11.68)</option>
    </select>
    <div id="textInputDiv" class="hidden">
      <label>Write your text below:</label>
      <textarea id="mugText" required></textarea>
    </div>
  </div>

  <div class="price" id="totalPrice">Total Price: $0.00</div>
  <button class="btn" type="button" onclick="goToPage(3)">Proceed to Buy</button>
</div>

<!-- Page 3: Shipping Info -->
<div class="container hidden" id="page3">
  <h2>Shipping Details</h2>
  <label>Full Name:</label>
  <input type="text" name="fullName" required>
  <label>Contact Number:</label>
  <input type="tel" name="contact" required>
  <label>Email:</label>
  <input type="email" name="email" required>
  <label>Shipping Address:</label>
  <textarea name="address" required></textarea>
  <button class="btn" type="button" onclick="goToPage(4)">Go to Payment</button>
</div>

<!-- Page 4: Payment -->
<div class="container hidden" id="page4">
  <h2>Payment</h2>
  <p>Google Pay: <strong>6352177416@ptaxis</strong></p>
  <p>PayPal: <a href="https://www.paypal.me/KavitaVarma883" target="_blank">Click here to pay</a></p>
  <p><em>Please complete the payment before confirming.</em></p>
  <button class="btn" type="button" onclick="goToPage(5)">I’ve Paid</button>
</div>

<!-- Page 5: Confirmation -->
<div class="container hidden" id="page5">
  <h2>Thank You!</h2>
  <p>Your order is confirmed. We’re so excited to make your magical mug!</p>
</div>

  </form>  <script>
    let total = 0;

    function goToPage(pageNum) {
      document.querySelectorAll('.container').forEach(c => c.classList.add('hidden'));
      document.getElementById('page' + pageNum).classList.remove('hidden');
      updatePrice();
    }

    function updatePrice() {
      total = 0;
      document.querySelectorAll('select').forEach(sel => {
        const price = parseFloat(sel.selectedOptions[0].getAttribute('data-price')) || 0;
        total += price;
      });
      document.getElementById('totalPrice').textContent = 'Total Price: $' + total.toFixed(2);
    }

    function togglePortraitUpload(val) {
      const uploadDiv = document.getElementById('portraitUpload');
      if (val === 'none') {
        uploadDiv.classList.add('hidden');
        document.getElementById('portraitFile').required = false;
      } else {
        uploadDiv.classList.remove('hidden');
        document.getElementById('portraitFile').required = true;
      }
      updatePrice();
    }

    function toggleTextInput(val) {
      const textDiv = document.getElementById('textInputDiv');
      if (val === 'none') {
        textDiv.classList.add('hidden');
        document.getElementById('mugText').required = false;
      } else {
        textDiv.classList.remove('hidden');
        document.getElementById('mugText').required = true;
      }
      updatePrice();
    }

    document.addEventListener('DOMContentLoaded', () => updatePrice());
  </script></body>
</html>
