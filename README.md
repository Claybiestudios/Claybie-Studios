<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Claybie Mug Customizer</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background-color: #f8f1ea;
      color: #9f2b2b;
      padding: 20px;
      max-width: 800px;
      margin: auto;
    }
    h1, h2, h3, label {
      color: #9f2b2b;
    }
    .page {
      display: none;
    }
    .visible {
      display: block;
    }
    .question {
      margin-bottom: 20px;
    }
    button {
      background-color: #9f2b2b;
      color: white;
      border: none;
      padding: 10px 20px;
      cursor: pointer;
      border-radius: 10px;
    }
    input[type="file"], input[type="text"], input[type="email"], input[type="tel"], textarea {
      width: 100%;
      padding: 8px;
      margin-top: 5px;
      margin-bottom: 10px;
      border: 1px solid #ddd;
      border-radius: 5px;
    }
    select {
      width: 100%;
      padding: 8px;
      margin-bottom: 10px;
      border-radius: 5px;
    }
    .price {
      font-size: 1.2em;
      margin-top: 20px;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <div id="page1" class="page visible">
    <h1>Welcome to Claybie</h1>
    <p>
      At Claybie, your mug becomes your world ✨ We turn cozy cups into magical moments—with Ghibli-style portraits 🌸, anime character vibes 🎌, and even designs inspired by your fave K-pop idol 🎤. Everything’s handmade, personalized, and totally aesthetic ☁️. So if you’ve ever dreamed of sipping from a cup that looks like it walked out of a Studio Ghibli scene or your favourite idols' MV—welcome home.
    </p>
    <button onclick="nextPage(1)">Customize Your Mug</button>
  </div>  <div id="page2" class="page">
    <form id="customForm">
      <h2>Customize Your Mug</h2>
      <div class="question">
        <label>Want portrait on your mug?</label>
        <select id="portraitOption" required onchange="togglePortraitUpload()">
          <option value="">--Choose--</option>
          <option value="11.63">1 portrait (+$11.63)</option>
          <option value="21.01">2 portraits (+$21.01)</option>
          <option value="0">None</option>
        </select>
        <div id="portraitUploadDiv" style="display:none">
          <label>Upload your portrait</label>
          <input type="file" id="portraitUpload" accept="image/*" required />
        </div>
      </div><div class="question">
    <label>Pick your cute 3D decorations (outside of the mug, small)</label>
    <select onchange="updatePrice(this)">
      <option value="0">--Choose--</option>
      <option value="5.83">small bow 🎀</option>
      <option value="9.34">3 medium size bows 🎀</option>
      <option value="3.50">heart ❤️</option>
      <option value="8.17">cherry 🍒</option>
      <option value="7.01">strawberry 🍓</option>
      <option value="11.68">cat footprint 🐾</option>
      <option value="11.68">dog footprint 🐾</option>
      <option value="9.34">teddy bear 🧸</option>
      <option value="7.01">butterfly 🦋</option>
    </select>
  </div>

  <div class="question">
    <label>Want a big 3D outside the mug?</label>
    <select onchange="updatePrice(this)">
      <option value="0">--Choose--</option>
      <option value="17.51">Giant bow 🎀❤️</option>
    </select>
  </div>

  <div class="question">
    <label>Add 3D elements inside the mug (base area)</label>
    <select onchange="updatePrice(this)">
      <option value="0">--Choose--</option>
      <option value="3.50">bow 🎀</option>
      <option value="2.34">heart ❤️</option>
      <option value="5.84">cherry 🍒</option>
      <option value="5.84">strawberry 🍓</option>
      <option value="3.50">cat footprint 🐾</option>
      <option value="3.50">dog footprint 🐾</option>
      <option value="11.68">cat 😺</option>
      <option value="11.68">dog 😺</option>
      <option value="7.01">butterfly 🦋</option>
    </select>
  </div>

  <div class="question">
    <label>Decorate the handle?</label>
    <select onchange="updatePrice(this)">
      <option value="0">--Choose--</option>
      <option value="7.01">bow 🎀</option>
      <option value="9.34">cat, on the handle 😺</option>
      <option value="9.34">dog, on the handle 🐶</option>
    </select>
  </div>

  <div class="question">
    <label>Wanna add text to your mug?</label>
    <select id="textOption" required onchange="toggleTextInput()">
      <option value="0">None</option>
      <option value="5.84">Inside the mug</option>
      <option value="8.17">Outside the mug</option>
      <option value="11.68">Both inside and outside</option>
    </select>
    <div id="textInputDiv" style="display:none">
      <label>Write your text</label>
      <textarea id="textInput" required></textarea>
    </div>
  </div>

  <div class="price" id="totalPrice">Total Price: $46.69</div>
  <button type="button" onclick="nextPage(2)">Next</button>
</form>

  </div>  <div id="page3" class="page">
    <h2>Shipping Details</h2>
    <form id="shippingForm">
      <label>Full Name</label>
      <input type="text" required />
      <label>Contact Number</label>
      <input type="tel" required />
      <label>Email</label>
      <input type="email" required />
      <label>Shipping Address</label>
      <textarea required></textarea>
      <button type="button" onclick="nextPage(3)">Next</button>
    </form>
  </div>  <div id="page4" class="page">
    <h2>Payment</h2>
    <p>Choose your payment method:</p>
    <ul>
      <li><strong>PayPal:</strong> <a href="https://www.paypal.me/KavitaVarma883" target="_blank">Click to pay</a></li>
      <li><strong>Paytm (Google Pay UPI):</strong> 6352177416@ptaxis</li>
    </ul>
    <button onclick="nextPage(4)">Done Payment</button>
  </div>  <div id="page5" class="page">
    <h2>Thanks for ordering!</h2>
    <p>Your order is confirmed. You're a real one, darling.</p>
  </div>  <script>
    let basePrice = 46.69;
    let total = basePrice;
    document.getElementById("totalPrice").innerText = `Total Price: $${total.toFixed(2)}`;

    function updatePrice(select) {
      const value = parseFloat(select.value);
      if (!isNaN(value)) {
        total += value;
        document.getElementById("totalPrice").innerText = `Total Price: $${total.toFixed(2)}`;
      }
    }

    function togglePortraitUpload() {
      const val = document.getElementById("portraitOption").value;
      const div = document.getElementById("portraitUploadDiv");
      div.style.display = val === "0" || val === "" ? "none" : "block";
    }

    function toggleTextInput() {
      const val = document.getElementById("textOption").value;
      const div = document.getElementById("textInputDiv");
      div.style.display = val === "0" ? "none" : "block";
    }

    function nextPage(current) {
      document.getElementById(`page${current}`).classList.remove("visible");
      document.getElementById(`page${current + 1}`).classList.add("visible");
    }
  </script></body>
</html>
