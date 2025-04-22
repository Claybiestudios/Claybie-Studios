<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Claybie Mug Customizer</title>
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background-color: #f8f1e7;
      color: #800020;
      margin: 0;
      padding: 0;
    }
    .container {
      max-width: 700px;
      margin: 0 auto;
      padding: 20px;
    }
    h1, h2 {
      text-align: center;
    }
    .question {
      margin-bottom: 20px;
    }
    .question label {
      display: block;
      margin-top: 10px;
    }
    .hidden {
      display: none;
    }
    .total {
      font-size: 1.2rem;
      font-weight: bold;
      margin: 20px 0;
      text-align: center;
    }
    button {
      background-color: #800020;
      color: white;
      border: none;
      padding: 10px 20px;
      font-size: 1rem;
      border-radius: 8px;
      cursor: pointer;
      margin: 10px auto;
      display: block;
    }
    button:hover {
      background-color: #a52a2a;
    }
    input, textarea, select {
      width: 100%;
      padding: 8px;
      margin-top: 5px;
      border: 1px solid #ccc;
      border-radius: 5px;
    }
    .step {
      display: none;
    }
    .step.active {
      display: block;
    }
    .payment-links a {
      display: block;
      margin: 10px 0;
      color: #800020;
      font-weight: bold;
      text-align: center;
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="step active" id="step1">
      <h1>Welcome to Claybie</h1>
      <p>At Claybie, your mug becomes your world. ✨<br>
        We turn cozy cups into magical moments—with Ghibli-style portraits 🌸, anime character vibes 🎌, and even designs inspired by your fave K-pop idol 🎤.<br>
        Everything’s handmade, personalized, and totally aesthetic ☁️. If you’ve ever dreamed of sipping from a cup that looks like it walked out of a Studio Ghibli scene or your favourite idols' MV—welcome home.</p>
      <button onclick="nextStep()">Start Customizing</button>
    </div><form id="customForm">
  <div class="step" id="step2">
    <h2>Customize Your Mug</h2>

    <div class="question">
      <label>Want portrait on your mug?</label>
      <label><input type="radio" name="portrait" value="11.63"> 1 portrait (+$11.63)</label>
      <label><input type="radio" name="portrait" value="21.01"> 2 portraits (+$21.01)</label>
      <label><input type="radio" name="portrait" value="0"> None</label>
      <div id="portraitUpload" class="hidden">
        <label>Upload your portrait:<input type="file" id="portraitFile"></label>
      </div>
    </div>

    <div class="question">
      <label>Pick your cute 3D decorations (outside):</label>
      <select name="smallDecor">
        <option value="0">None</option>
        <option value="5.83">Small bow 🎀 (+$5.83)</option>
        <option value="9.34">3 medium bows 🎀 (+$9.34)</option>
        <option value="3.50">Heart ❤️ (+$3.50)</option>
        <option value="8.17">Cherry 🍒 (+$8.17)</option>
        <option value="7.01">Strawberry 🍓 (+$7.01)</option>
        <option value="11.68">Cat paw 🐾 (+$11.68)</option>
        <option value="11.68">Dog paw 🐾 (+$11.68)</option>
        <option value="9.34">Teddy bear 🧸 (+$9.34)</option>
        <option value="7.01">Butterfly 🦋 (+$7.01)</option>
      </select>
    </div>

    <div class="question">
      <label>Want a big 3D outside the mug?</label>
      <select name="giantDecor">
        <option value="0">None</option>
        <option value="17.51">Giant Bow 🎀❤️ (+$17.51)</option>
      </select>
    </div>

    <div class="question">
      <label>Add 3D inside the mug (base):</label>
      <select name="insideDecor">
        <option value="0">None</option>
        <option value="3.50">Bow 🎀 (+$3.50)</option>
        <option value="2.34">Heart ❤️ (+$2.34)</option>
        <option value="5.84">Cherry 🍒 (+$5.84)</option>
        <option value="5.84">Strawberry 🍓 (+$5.84)</option>
        <option value="3.50">Cat paw 🐾 (+$3.50)</option>
        <option value="3.50">Dog paw 🐾 (+$3.50)</option>
        <option value="11.68">Cat 😺 (+$11.68)</option>
        <option value="11.68">Dog 🐶 (+$11.68)</option>
        <option value="7.01">Butterfly 🦋 (+$7.01)</option>
      </select>
    </div>

    <div class="question">
      <label>Decorate the handle?</label>
      <select name="handleDecor">
        <option value="0">None</option>
        <option value="7.01">Bow 🎀 (+$7.01)</option>
        <option value="9.34">Cat 😺 (+$9.34)</option>
        <option value="9.34">Dog 🐶 (+$9.34)</option>
      </select>
    </div>

    <div class="question">
      <label>Wanna add text to your mug?</label>
      <select name="textOption" id="textOption">
        <option value="0">None</option>
        <option value="5.84">Inside the mug (+$5.84)</option>
        <option value="8.17">Outside the mug (+$8.17)</option>
        <option value="11.68">Both (+$11.68)</option>
      </select>
      <div id="textInputWrap" class="hidden">
        <label>Write your text:<textarea id="customText"></textarea></label>
      </div>
    </div>

    <div class="total">Total: $<span id="totalPrice">0.00</span></div>
    <button type="button" onclick="nextStep()">Next</button>
  </div>

  <div class="step" id="step3">
    <h2>Shipping Info</h2>
    <label>Full Name: <input type="text" required></label>
    <label>Contact Number: <input type="text" required></label>
    <label>Email: <input type="email" required></label>
    <label>Shipping Address: <textarea required></textarea></label>
    <button type="button" onclick="nextStep()">Proceed to Payment</button>
  </div>

  <div class="step" id="step4">
    <h2>Payment</h2>
    <div class="payment-links">
      <a href="upi://pay?pa=6352177416@ptaxis&pn=Claybie&cu=INR" target="_blank">Pay with Google Pay</a>
      <a href="https://www.paypal.me/KavitaVarma883" target="_blank">Pay with PayPal</a>
    </div>
    <button type="button" onclick="nextStep()">I've Paid</button>
  </div>

  <div class="step" id="step5">
    <h2>Thanks for ordering!</h2>
    <p>Your order is confirmed. We’ll contact you soon with your magical mug update!</p>
  </div>
</form>

  </div>  <script>
    let currentStep = 0;
    const steps = document.querySelectorAll('.step');

    function nextStep() {
      steps[currentStep].classList.remove('active');
      currentStep++;
      if (steps[currentStep]) {
        steps[currentStep].classList.add('active');
      }
    }

    const form = document.getElementById('customForm');
    const totalPriceEl = document.getElementById('totalPrice');
    const portraitUpload = document.getElementById('portraitUpload');
    const textInputWrap = document.getElementById('textInputWrap');

    form.addEventListener('change', () => {
      let total = 0;
      const data = new FormData(form);
      for (let value of data.values()) {
        if (!isNaN(parseFloat(value))) {
          total += parseFloat(value);
        }
      }
      totalPriceEl.textContent = total.toFixed(2);

      const portraitVal = data.get("portrait");
      if (portraitVal && parseFloat(portraitVal) > 0) {
        portraitUpload.classList.remove("hidden");
        document.getElementById("portraitFile").setAttribute("required", "true");
      } else {
        portraitUpload.classList.add("hidden");
        document.getElementById("portraitFile").removeAttribute("required");
      }

      const textVal = data.get("textOption");
      if (textVal && parseFloat(textVal) > 0) {
        textInputWrap.classList.remove("hidden");
        document.getElementById("customText").setAttribute("required", "true");
      } else {
        textInputWrap.classList.add("hidden");
        document.getElementById("customText").removeAttribute("required");
      }
    });
  </script></body>
</html>
