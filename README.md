<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Claybie Mug Customizer</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background-color: #f8f1e7;
      color: #6a1b1a;
      margin: 0;
      padding: 0;
    }
    .container {
      max-width: 700px;
      margin: auto;
      padding: 20px;
    }
    h1, h2 {
      color: #6a1b1a;
    }
    .hidden {
      display: none;
    }
    label {
      display: block;
      margin: 10px 0 5px;
    }
    input[type="text"], input[type="email"], input[type="file"], textarea {
      width: 100%;
      padding: 8px;
      margin-bottom: 10px;
      border: 1px solid #ccc;
      border-radius: 5px;
    }
    button {
      background-color: #6a1b1a;
      color: white;
      padding: 10px 20px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      margin: 10px 0;
    }
    button:hover {
      background-color: #8e2e2c;
    }
  </style>
</head>
<body>
<div class="container" id="page1">
  <h1>Welcome to Claybie</h1>
  <p>At Claybie, your mug becomes your world ✨<br>
    We turn cozy cups into magical moments—with Ghibli-style portraits 🌸, anime character vibes 🎌, and even designs inspired by your fave K-pop idol 🎤.<br>
    Everything’s handmade, personalized, and totally aesthetic ☁️.<br>
    So if you’ve ever dreamed of sipping from a cup that looks like it walked out of a Studio Ghibli scene or your favourite idols' MV—welcome home.</p>
  <button onclick="nextPage(2)">Next</button>
</div><div class="container hidden" id="page2">
  <h2>Customize Your Mug</h2>
  <form id="customForm">
    <label>Want portrait on your mug?</label>
    <select name="portrait" onchange="togglePortraitUpload(this.value)">
      <option value="none">None</option>
      <option value="1">1 portrait (+$11.63)</option>
      <option value="2">2 portraits (+$21.01)</option>
    </select>
    <div id="portraitUpload" class="hidden">
      <label>Upload your portrait</label>
      <input type="file" name="portraitImage" id="portraitImage" />
    </div><label>Pick your cute 3D decorations (outside):</label>
<select name="decorOutside" onchange="updatePrice()">
  <option value="none">None</option>
  <option value="small_bow">Small bow 🎀 (+$5.83)</option>
  <option value="3_bows">3 medium bows 🎀 (+$9.34)</option>
  <option value="heart">Heart ❤️ (+$3.50)</option>
  <option value="cherry">Cherry 🍒 (+$8.17)</option>
  <option value="strawberry">Strawberry 🍓 (+$7.01)</option>
  <option value="cat_foot">Cat footprint 🐾 (+$11.68)</option>
  <option value="dog_foot">Dog footprint 🐾 (+$11.68)</option>
  <option value="teddy">Teddy bear 🧸 (+$9.34)</option>
  <option value="butterfly">Butterfly 🦋 (+$7.01)</option>
</select>

<label>Want a big 3D outside the mug?</label>
<select name="big3d" onchange="updatePrice()">
  <option value="none">None</option>
  <option value="giant_bow">Giant bow 🎀❤️ (+$17.51)</option>
</select>

<label>Add 3D elements inside the mug:</label>
<select name="inside3d" onchange="updatePrice()">
  <option value="none">None</option>
  <option value="bow">Bow 🎀 (+$3.50)</option>
  <option value="heart">Heart ❤️ (+$2.34)</option>
  <option value="cherry">Cherry 🍒 (+$5.84)</option>
  <option value="strawberry">Strawberry 🍓 (+$5.84)</option>
  <option value="cat_foot">Cat footprint 🐾 (+$3.50)</option>
  <option value="dog_foot">Dog footprint 🐾 (+$3.50)</option>
  <option value="cat">Cat 😺 (+$11.68)</option>
  <option value="dog">Dog 😺 (+$11.68)</option>
  <option value="butterfly">Butterfly 🦋 (+$7.01)</option>
</select>

<label>Decorate the handle?</label>
<select name="handle" onchange="updatePrice()">
  <option value="none">None</option>
  <option value="bow">Bow 🎀 (+$7.01)</option>
  <option value="cat">Cat 😺 (+$9.34)</option>
  <option value="dog">Dog 🐶 (+$9.34)</option>
</select>

<label>Wanna add text to your mug?</label>
<select name="textOption" onchange="toggleTextBox(this.value)">
  <option value="none">None</option>
  <option value="inside">Inside the mug (+$5.84)</option>
  <option value="outside">Outside the mug (+$8.17)</option>
  <option value="both">Both (+$11.68)</option>
</select>
<div id="textBox" class="hidden">
  <label>Write your text below</label>
  <textarea name="customText" required></textarea>
</div>
<p><strong>Total Price: $<span id="totalPrice">46.69</span></strong></p>
<button type="button" onclick="nextPage(3)">Proceed to Buy</button>

  </form>
</div><div class="container hidden" id="page3">
  <h2>Shipping Details</h2>
  <label>Full Name</label>
  <input type="text" required />
  <label>Contact Number</label>
  <input type="text" required />
  <label>Email</label>
  <input type="email" required />
  <label>Shipping Address</label>
  <textarea required></textarea>
  <button onclick="nextPage(4)">Next</button>
</div><div class="container hidden" id="page4">
  <h2>Payment</h2>
  <p>Google Pay: <strong>6352177416@ptaxis</strong></p>
  <p>PayPal: <a href="https://www.paypal.me/KavitaVarma883" target="_blank">Pay Now</a></p>
  <p>After payment is done, click below to confirm:</p>
  <button onclick="nextPage(5)">I Have Paid</button>
</div><div class="container hidden" id="page5">
  <h2>Thanks for Ordering!</h2>
  <p>Your order is confirmed. We’re already brewing up the magic!</p>
</div><script>
  let basePrice = 46.69;

  function nextPage(pageNumber) {
    document.querySelectorAll(".container").forEach(p => p.classList.add("hidden"));
    document.getElementById("page" + pageNumber).classList.remove("hidden");
  }

  function togglePortraitUpload(value) {
    const upload = document.getElementById("portraitUpload");
    const portraitInput = document.getElementById("portraitImage");
    if (value !== "none") {
      upload.classList.remove("hidden");
      portraitInput.required = true;
    } else {
      upload.classList.add("hidden");
      portraitInput.required = false;
    }
    updatePrice();
  }

  function toggleTextBox(value) {
    const textBox = document.getElementById("textBox");
    if (value !== "none") {
      textBox.classList.remove("hidden");
    } else {
      textBox.classList.add("hidden");
    }
    updatePrice();
  }

  function updatePrice() {
    let price = basePrice;
    const portrait = document.querySelector("select[name='portrait']").value;
    if (portrait === "1") price += 11.63;
    if (portrait === "2") price += 21.01;

    const priceMap = {
      small_bow: 5.83, "3_bows": 9.34, heart: 3.5, cherry: 8.17,
      strawberry: 7.01, cat_foot: 11.68, dog_foot: 11.68, teddy: 9.34,
      butterfly: 7.01, giant_bow: 17.51, bow: 3.5, cat: 11.68, dog: 11.68
    };

    ["decorOutside", "big3d", "inside3d", "handle"].forEach(name => {
      const val = document.querySelector(`select[name='${name}']`).value;
      if (priceMap[val]) price += priceMap[val];
    });

    const textOption = document.querySelector("select[name='textOption']").value;
    if (textOption === "inside") price += 5.84;
    if (textOption === "outside") price += 8.17;
    if (textOption === "both") price += 11.68;

    document.getElementById("totalPrice").innerText = price.toFixed(2);
  }
</script></body>
</html>