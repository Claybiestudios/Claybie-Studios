<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Claybie</title>
  <style>
    body {
      font-family: 'Comic Sans MS', cursive;
      background-color: #f5f0e6;
      color: #8b0000;
      padding: 20px;
      max-width: 800px;
      margin: auto;
    }
    h1, h2, h3, label {
      color: #a30000;
    }
    button, input[type="submit"] {
      background-color: #a30000;
      color: white;
      border: none;
      padding: 10px 20px;
      margin: 10px 0;
      cursor: pointer;
      border-radius: 10px;
    }
    input, select, textarea {
      display: block;
      width: 100%;
      padding: 10px;
      margin-bottom: 20px;
      border-radius: 5px;
      border: 1px solid #ccc;
    }
    .hidden {
      display: none;
    }
    .price {
      font-size: 1.2em;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <div id="page1">
    <h1>Welcome to Claybie!</h1>
    <p>
      At Claybie, your mug becomes your world ✨ We turn cozy cups into magical moments — with Ghibli-style portraits 🌸, anime character vibes 🎌, and even designs inspired by your fave K-pop idol 🎤. Everything’s handmade, personalized, and totally aesthetic ☁️.
    </p>
    <p>
      So if you’ve ever dreamed of sipping from a cup that looks like it walked out of a Studio Ghibli scene or your favourite idols' MV — welcome home.
    </p>
    <button onclick="nextPage(2)">Start Designing</button>
  </div>  <form id="page2" class="hidden">
    <h2>Customize Your Mug</h2><label>1. Want portrait on your mug?</label>
<select id="portrait" onchange="togglePortraitUpload(); calculateTotal();">
  <option value="0">None</option>
  <option value="11.63">1 portrait (+$11.63)</option>
  <option value="21.01">2 portraits (+$21.01)</option>
</select>

<div id="portraitUpload" class="hidden">
  <label>Upload your portrait:</label>
  <input type="file" id="portraitFile" accept="image/*" required />
</div>

<label>2. Pick your cute 3D decorations (outside of the mug, small)</label>
<select onchange="calculateTotal();">
  <option value="0">None</option>
  <option value="5.83">small bow 🎀 (+$5.83)</option>
  <option value="9.34">3 medium bows 🎀 (+$9.34)</option>
  <option value="3.5">heart ❤️ (+$3.50)</option>
  <option value="8.17">cherry 🍒 (+$8.17)</option>
  <option value="7.01">strawberry 🍓 (+$7.01)</option>
  <option value="11.68">cat footprint 🐾 (+$11.68)</option>
  <option value="11.68">dog footprint 🐾 (+$11.68)</option>
  <option value="9.34">teddy bear 🧸 (+$9.34)</option>
  <option value="7.01">butterfly 🦋 (+$7.01)</option>
</select>

<label>3. Want a big 3D outside the mug?</label>
<select onchange="calculateTotal();">
  <option value="0">None</option>
  <option value="17.51">Giant bow 🎀❤️ (+$17.51)</option>
</select>

<label>4. Add 3D elements inside the mug (base area)</label>
<select onchange="calculateTotal();">
  <option value="0">None</option>
  <option value="3.5">bow 🎀 (+$3.50)</option>
  <option value="2.34">heart ❤️ (+$2.34)</option>
  <option value="5.84">cherry 🍒 (+$5.84)</option>
  <option value="5.84">strawberry 🍓 (+$5.84)</option>
  <option value="3.5">cat footprint 🐾 (+$3.50)</option>
  <option value="3.5">dog footprint 🐾 (+$3.50)</option>
  <option value="11.68">cat 😺 (+$11.68)</option>
  <option value="11.68">dog 😺 (+$11.68)</option>
  <option value="7.01">butterfly 🦋 (+$7.01)</option>
</select>

<label>5. Decorate the handle?</label>
<select onchange="calculateTotal();">
  <option value="0">None</option>
  <option value="7.01">bow 🎀 (+$7.01)</option>
  <option value="9.34">cat, on handle 😺 (+$9.34)</option>
  <option value="9.34">dog, on handle 🐶 (+$9.34)</option>
</select>

<label>6. Wanna add text to your mug?</label>
<select id="textOption" onchange="toggleTextInput(); calculateTotal();">
  <option value="0">None</option>
  <option value="5.84">Inside the mug (+$5.84)</option>
  <option value="8.17">Outside the mug (+$8.17)</option>
  <option value="11.68">Both inside & outside (+$11.68)</option>
</select>

<div id="textInput" class="hidden">
  <label>Write your text:</label>
  <textarea id="customText" required></textarea>
</div>

<div class="price" id="totalPrice">Total Price: $0.00</div>

<button type="button" onclick="nextPage(3)">Proceed to Buy</button>

  </form>  <form id="page3" class="hidden">
    <h2>Shipping Details</h2>
    <label>Full name:</label>
    <input type="text" required />
    <label>Contact number:</label>
    <input type="tel" required />
    <label>Email:</label>
    <input type="email" required />
    <label>Shipping address:</label>
    <textarea required></textarea>
    <button type="button" onclick="nextPage(4)">Proceed to Payment</button>
  </form>  <div id="page4" class="hidden">
    <h2>Payment</h2>
    <p>Choose your payment method:</p>
    <p>Google Pay: <strong>6352177416@ptaxis</strong></p>
    <p>PayPal: <a href="https://www.paypal.me/KavitaVarma883" target="_blank">Click here to pay</a></p>
    <button onclick="nextPage(5)">I’ve Paid</button>
  </div>  <div id="page5" class="hidden">
    <h2>Thanks for ordering!</h2>
    <p>Your order is confirmed. We'll get working on your cozy kawaii mug ASAP!</p>
  </div>  <script>
    let total = 0;

    function nextPage(num) {
      for (let i = 1; i <= 5; i++) {
        document.getElementById("page" + i).classList.add("hidden");
      }
      document.getElementById("page" + num).classList.remove("hidden");
    }

    function togglePortraitUpload() {
      const portrait = document.getElementById("portrait").value;
      const upload = document.getElementById("portraitUpload");
      if (parseFloat(portrait) > 0) {
        upload.classList.remove("hidden");
        document.getElementById("portraitFile").required = true;
      } else {
        upload.classList.add("hidden");
        document.getElementById("portraitFile").required = false;
      }
    }

    function toggleTextInput() {
      const text = document.getElementById("textOption").value;
      const input = document.getElementById("textInput");
      if (parseFloat(text) > 0) {
        input.classList.remove("hidden");
        document.getElementById("customText").required = true;
      } else {
        input.classList.add("hidden");
        document.getElementById("customText").required = false;
      }
    }

    function calculateTotal() {
      const selects = document.querySelectorAll("#page2 select");
      total = 0;
      selects.forEach(sel => {
        total += parseFloat(sel.value);
      });
      document.getElementById("totalPrice").innerText = `Total Price: $${total.toFixed(2)}`;
    }
  </script></body>
</html>
