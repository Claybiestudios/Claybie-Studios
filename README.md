<!DOCTYPE html><html lang="en">
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
<body><!-- Page 1 --><section id="page1">
  <h1>Welcome to Claybie!</h1>
  <p>
    At Claybie, your mug becomes your world ✨<br>
    We turn cozy cups into magical moments—with Ghibli-style portraits 🌸,
    anime character vibes 🎌, and even designs inspired by your fave K-pop idol 🎤.<br>
    Everything’s handmade, personalized, and totally aesthetic ☁️.<br>
    So if you’ve ever dreamed of sipping from a cup that looks like it walked out of a Studio Ghibli scene or your favourite idols' MV—welcome home.
  </p>
  <button class="button" onclick="nextPage('page1','page2')">Customize Your Mug</button>
</section><!-- Page 2 - Customization Form --><section id="page2" class="hidden">
  <h2>Mug Customization</h2>
  <form id="customForm">
    <input type="hidden" id="basePrice" value="46.69"><!-- Question 1 -->
<label>Want portrait on your mug?</label>
<select id="portrait" name="portrait" required onchange="handlePortrait(this.value)">
  <option value="">--Select--</option>
  <option value="1" data-price="11.63">1 portrait</option>
  <option value="2" data-price="21.01">2 portraits</option>
  <option value="none" data-price="0">No portrait</option>
</select>

<div id="portraitUpload" class="hidden">
  <label>Upload your portrait</label>
  <input type="file" name="portraitFile" id="portraitFile" accept="image/*">
</div>

<!-- Question 2 -->
<label>Pick your cute 3D decorations (outside of the mug, small)</label>
<select id="decorSmall" name="decorSmall" required>
  <option value="">--Select--</option>
  <option data-price="5.83">small bow 🎀</option>
  <option data-price="9.34">3 medium size bows 🎀</option>
  <option data-price="3.50">heart ❤️</option>
  <option data-price="8.17">cherry 🍒</option>
  <option data-price="7.01">strawberry 🍓</option>
  <option data-price="11.68">cat footprint 🐾</option>
  <option data-price="11.68">dog footprint 🐾</option>
  <option data-price="9.34">teddy bear 🧸</option>
  <option data-price="7.01">butterfly 🦋</option>
</select>

<!-- Question 3 -->
<label>Want a big 3D outside the mug?</label>
<select id="decorBig" name="decorBig" required>
  <option value="">--Select--</option>
  <option data-price="17.51">Giant bow 🎀❤️</option>
</select>

<!-- Question 4 -->
<label>Add 3D elements inside the mug (base area)</label>
<select id="decorInside" name="decorInside" required>
  <option value="">--Select--</option>
  <option data-price="3.50">bow 🎀</option>
  <option data-price="2.34">heart ❤️</option>
  <option data-price="5.84">cherry 🍒</option>
  <option data-price="5.84">strawberry 🍓</option>
  <option data-price="3.50">cat footprint 🐾</option>
  <option data-price="3.50">dog footprint 🐾</option>
  <option data-price="11.68">cat 😺</option>
  <option data-price="11.68">dog 😺</option>
  <option data-price="7.01">butterfly 🦋</option>
</select>

<!-- Question 5 -->
<label>Decorate the handle?</label>
<select id="handleDecor" name="handleDecor" required>
  <option value="">--Select--</option>
  <option data-price="7.01">bow 🎀</option>
  <option data-price="9.34">cat, on the handle 😺</option>
  <option data-price="9.34">dog, on the handle 🐶</option>
</select>

<!-- Question 6 -->
<label>Wanna add text to your mug?</label>
<select id="textOption" name="textOption" required onchange="handleText(this.value)">
  <option value="">--Select--</option>
  <option value="inside" data-price="5.84">Inside the mug</option>
  <option value="outside" data-price="8.17">Outside the mug</option>
  <option value="both" data-price="11.68">Both inside and outside</option>
  <option value="none" data-price="0">No text</option>
</select>

<div id="textInput" class="hidden">
  <label>Write your text below</label>
  <textarea name="customText" id="customText" required></textarea>
</div>

<h3>Total Price: $<span id="totalPrice">46.69</span></h3>
<button type="button" class="button" onclick="nextPage('page2','page3')">Next</button>

  </form>
</section><!-- Page 3 - Contact Info --><section id="page3" class="hidden">
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
</section><!-- Page 4 - Payment --><section id="page4" class="hidden">
  <h2>Payment</h2>
  <p>Choose a payment method:</p>
  <p><strong>Google Pay:</strong> 6352177416@ptaxis</p>
  <p><strong>PayPal:</strong> <a href="https://www.paypal.me/KavitaVarma883" target="_blank">paypal.me/KavitaVarma883</a></p>
  <p>Once payment is done, click below to confirm:</p>
  <button class="button" onclick="nextPage('page4','page5')">I Have Paid</button>
</section><!-- Page 5 - Confirmation --><section id="page5" class="hidden">
  <h2>Thank you for ordering!</h2>
  <p>Your order is confirmed. You’re the best!</p>
</section><script>
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
</script></body>
</html>
