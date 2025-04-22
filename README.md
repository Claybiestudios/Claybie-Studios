<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Claybie Mug Customizer</title>
  <style>
    body {
      margin: 0;
      font-family: 'Poppins', sans-serif;
      background-color: #f9f5f0;
      color: #3b1f2b;
    }
    .page {
      display: none;
      padding: 2rem;
    }
    .active {
      display: block;
    }
    .button {
      background-color: #8b2d3c;
      color: #fff;
      padding: 10px 20px;
      border: none;
      cursor: pointer;
      margin-top: 20px;
    }
    .button:hover {
      background-color: #6e222f;
    }
    input[type="text"], input[type="email"], input[type="tel"], textarea, select {
      width: 100%;
      padding: 10px;
      margin: 10px 0;
      border: 1px solid #ccc;
      border-radius: 5px;
      font-size: 1rem;
    }
    .hidden { display: none; }
    h2, h3 { color: #8b2d3c; }
  </style>
</head>
<body><div id="page1" class="page active">
  <h2>Welcome to Claybie</h2>
  <p>At Claybie, your mug becomes your world ✨<br>We turn cozy cups into magical moments—with Ghibli-style portraits 🌸, anime character vibes 🎌, and even designs inspired by your fave K-pop idol 🎤. Everything’s handmade, personalized, and totally aesthetic ☁️. So if you’ve ever dreamed of sipping from a cup that looks like it walked out of a Studio Ghibli scene or your favourite idols' MV—welcome home.</p>
  <button class="button" onclick="nextPage('page1', 'page2')">Customize Your Mug</button>
</div><div id="page2" class="page">
  <form id="customForm">
    <h3>1. Want portrait on your mug?</h3>
    <label><input type="radio" name="portrait" value="1 portrait" data-price="11.63" required> 1 portrait (+$11.63)</label><br>
    <label><input type="radio" name="portrait" value="2 portrait" data-price="21.01"> 2 portrait (+$21.01)</label><br>
    <div id="uploadPortrait" class="hidden">
      <label>Upload your portrait <input type="file" id="portraitFile" required></label>
    </div><h3>2. Pick your cute 3D decorations (outside, small)</h3>
<select id="decorSmall" required>
  <option value="">Select</option>
  <option value="small bow 🎀" data-price="5.83">Small bow 🎀</option>
  <option value="3 medium bows 🎀" data-price="9.34">3 medium bows 🎀</option>
  <option value="heart ❤️" data-price="3.50">Heart ❤️</option>
  <option value="cherry 🍒" data-price="8.17">Cherry 🍒</option>
  <option value="strawberry 🍓" data-price="7.01">Strawberry 🍓</option>
  <option value="cat footprint 🐾" data-price="11.68">Cat footprint 🐾</option>
  <option value="dog footprint 🐾" data-price="11.68">Dog footprint 🐾</option>
  <option value="teddy bear 🧸" data-price="9.34">Teddy bear 🧸</option>
  <option value="butterfly 🦋" data-price="7.01">Butterfly 🦋</option>
</select>

<!-- Similar sections for Questions 3–6 here -->

<h3>Total Price: $<span id="totalPrice">46.69</span></h3>
<button type="button" class="button" onclick="nextPage('page2','page3')">Proceed to Buy</button>

  </form>
</div><div id="page3" class="page">
  <form id="infoForm">
    <h3>Full Name</h3>
    <input type="text" name="fullName" required>
    <h3>Contact Number</h3>
    <input type="tel" name="contactNumber" required>
    <h3>Email</h3>
    <input type="email" name="email" required>
    <h3>Shipping Address</h3>
    <textarea name="address" required></textarea>
    <button type="submit" class="button">Next</button>
  </form>
</div><div id="page4" class="page">
  <h3>Choose Payment Method</h3>
  <p><strong>Google Pay:</strong> 6352177416@ptaxis</p>
  <p><strong>PayPal:</strong> <a href="https://www.paypal.me/KavitaVarma883" target="_blank">paypal.me/KavitaVarma883</a></p>
  <button class="button" onclick="nextPage('page4','page5')">I’ve Completed Payment</button>
</div><div id="page5" class="page">
  <h2>Thanks for ordering!</h2>
  <p>Your order is confirmed. We’ll start crafting your magical mug soon!</p>
</div><script>
let basePrice = 46.69;
let totalPrice = basePrice;

const portraitOptions = document.querySelectorAll('input[name="portrait"]');
const portraitUpload = document.getElementById('uploadPortrait');

portraitOptions.forEach(option => {
  option.addEventListener('change', () => {
    if (option.checked) {
      portraitUpload.classList.remove('hidden');
      document.getElementById('portraitFile').required = true;
      updatePrice();
    }
  });
});

document.getElementById('decorSmall').addEventListener('change', updatePrice);

function updatePrice() {
  totalPrice = basePrice;
  const portrait = document.querySelector('input[name="portrait"]:checked');
  const decor = document.getElementById('decorSmall');

  if (portrait) totalPrice += parseFloat(portrait.dataset.price);
  if (decor && decor.selectedOptions[0].dataset.price) totalPrice += parseFloat(decor.selectedOptions[0].dataset.price);

  document.getElementById('totalPrice').innerText = totalPrice.toFixed(2);
}

function nextPage(current, next) {
  document.getElementById(current).classList.remove('active');
  document.getElementById(next).classList.add('active');
}

// FORM SUBMIT TO GOOGLE SHEETS
const infoForm = document.getElementById('infoForm');
infoForm.addEventListener('submit', function (e) {
  e.preventDefault();

  const formData = new FormData(infoForm);
  const data = {
    fullName: formData.get('fullName'),
    contactNumber: formData.get('contactNumber'),
    email: formData.get('email'),
    address: formData.get('address'),
    portrait: document.querySelector('input[name="portrait"]:checked')?.value || '',
    decorations: document.getElementById('decorSmall')?.value || '',
    totalPrice: document.getElementById('totalPrice').innerText
  };

  fetch("YOUR_GOOGLE_APPS_SCRIPT_URL", {
    method: 'POST',
    body: JSON.stringify(data)
  }).then(() => {
    nextPage('page3', 'page4');
  });
});
</script></body>
</html>