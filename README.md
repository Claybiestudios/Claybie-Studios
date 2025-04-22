<!DOCTYPE html><html lang="en"><head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Claybie Mug Customizer</title>
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background-color: #f5f1e7;
      color: #6d1c1c;
    }.container {
  max-width: 700px;
  margin: auto;
  padding: 2rem;
}

h1, h2 {
  color: #6d1c1c;
}

label, select, input, textarea {
  display: block;
  margin: 10px 0;
  width: 100%;
  padding: 8px;
  font-size: 1rem;
}

.question {
  margin: 1.5rem 0;
}

button {
  padding: 10px 20px;
  font-size: 1rem;
  background-color: #6d1c1c;
  color: #fff;
  border: none;
  cursor: pointer;
  border-radius: 5px;
}

.hidden {
  display: none;
}

.price-display {
  font-size: 1.2rem;
  font-weight: bold;
}

  </style>
</head><body>
  <div class="container" id="page1">
    <h1>Welcome to Claybie</h1>
    <p>At Claybie, your mug becomes your world ✨ We turn cozy cups into magical moments—with Ghibli-style portraits 🌸, anime character vibes 🎌, and even designs inspired by your fave K-pop idol 🎤. Everything’s handmade, personalized, and totally aesthetic ☁️. So if you’ve ever dreamed of sipping from a cup that looks like it walked out of a Studio Ghibli scene or your favourite idols' MV—welcome home.</p>
    <button onclick="goToPage(2)">Start Customizing</button>
  </div>  <form class="container hidden" id="page2">
    <h2>Customize Your Mug</h2><div class="question">
  <label>Want portrait on your mug?</label>
  <select name="portrait" required onchange="togglePortraitUpload(this.value)">
    <option value="none" data-price="0">None</option>
    <option value="1" data-price="11.63">1 portrait (+$11.63)</option>
    <option value="2" data-price="21.01">2 portraits (+$21.01)</option>
  </select>
</div>

<div id="portraitUpload" class="hidden">
  <label>Upload your portrait:</label>
  <input type="file" name="portraitFile" id="portraitFile">
</div>

<div class="question">
  <label>Pick your cute 3D decorations (outside of the mug, small):</label>
  <select name="outside3D" required onchange="updatePrice(this)">
    <option value="bow" data-price="5.83">Small bow 🎀 (+$5.83)</option>
    <option value="3bows" data-price="9.34">3 medium bows 🎀 (+$9.34)</option>
    <option value="heart" data-price="3.50">Heart ❤️ (+$3.50)</option>
    <option value="cherry" data-price="8.17">Cherry 🍒 (+$8.17)</option>
    <option value="strawberry" data-price="7.01">Strawberry 🍓 (+$7.01)</option>
    <option value="catpaw" data-price="11.68">Cat footprint 🐾 (+$11.68)</option>
    <option value="dogpaw" data-price="11.68">Dog footprint 🐾 (+$11.68)</option>
    <option value="teddy" data-price="9.34">Teddy bear 🧸 (+$9.34)</option>
    <option value="butterfly" data-price="7.01">Butterfly 🦋 (+$7.01)</option>
  </select>
</div>

<div class="question">
  <label>Want a big 3D outside the mug?</label>
  <select name="big3D" required onchange="updatePrice(this)">
    <option value="none" data-price="0">None</option>
    <option value="giantbow" data-price="17.51">Giant bow 🎀❤️ (+$17.51)</option>
  </select>
</div>

<div class="question">
  <label>Add 3D elements inside the mug (base area):</label>
  <select name="inside3D" required onchange="updatePrice(this)">
    <option value="bow" data-price="3.50">Bow 🎀 (+$3.50)</option>
    <option value="heart" data-price="2.34">Heart ❤️ (+$2.34)</option>
    <option value="cherry" data-price="5.84">Cherry 🍒 (+$5.84)</option>
    <option value="strawberry" data-price="5.84">Strawberry 🍓 (+$5.84)</option>
    <option value="catpaw" data-price="3.50">Cat footprint 🐾 (+$3.50)</option>
    <option value="dogpaw" data-price="3.50">Dog footprint 🐾 (+$3.50)</option>
    <option value="cat" data-price="11.68">Cat 😺 (+$11.68)</option>
    <option value="dog" data-price="11.68">Dog 😺 (+$11.68)</option>
    <option value="butterfly" data-price="7.01">Butterfly 🦋 (+$7.01)</option>
  </select>
</div>

<div class="question">
  <label>Decorate the handle?</label>
  <select name="handleDecor" required onchange="updatePrice(this)">
    <option value="bow" data-price="7.01">Bow 🎀 (+$7.01)</option>
    <option value="cat" data-price="9.34">Cat 😺 (+$9.34)</option>
    <option value="dog" data-price="9.34">Dog 🐶 (+$9.34)</option>
  </select>
</div>

<div class="question">
  <label>Wanna add text to your mug?</label>
  <select name="textOption" required onchange="toggleTextInput(this.value)">
    <option value="none" data-price="0">None</option>
    <option value="inside" data-price="5.84">Inside the mug (+$5.84)</option>
    <option value="outside" data-price="8.17">Outside the mug (+$8.17)</option>
    <option value="both" data-price="11.68">Both inside & outside (+$11.68)</option>
  </select>
</div>

<div id="textInput" class="hidden">
  <label>Write your text:</label>
  <textarea name="mugText" required></textarea>
</div>

<div class="price-display">Total Price: $<span id="totalPrice">46.69</span></div>
<button type="button" onclick="goToPage(3)">Next</button>

  </form>  <form class="container hidden" id="page3">
    <h2>Shipping Info</h2>
    <label>Full Name:</label>
    <input type="text" name="fullName" required><label>Contact Number:</label>
<input type="tel" name="phone" required>

<label>Email:</label>
<input type="email" name="email" required>

<label>Shipping Address:</label>
<textarea name="address" required></textarea>

<button type="button" onclick="goToPage(4)">Proceed to Payment</button>

  </form>  <div class="container hidden" id="page4">
    <h2>Payment</h2>
    <p>Total Amount: $<span id="finalAmount">46.69</span></p>
    <p>Pay via:</p>
    <p><strong>Google Pay:</strong> 6352177416@ptaxis</p>
    <p><strong>PayPal:</strong> <a href="https://www.paypal.me/KavitaVarma883" target="_blank">paypal.me/KavitaVarma883</a></p>
    <button onclick="goToPage(5)">I’ve Completed Payment</button>
  </div>  <div class="container hidden" id="page5">
    <h2>Thanks for ordering!</h2>
    <p>Your order is confirmed. Get ready for magical sips!</p>
  </div>  <script>
    let total = 46.69;

    function updatePrice(select) {
      calculateTotal();
    }

    function calculateTotal() {
      total = 46.69;
      document.querySelectorAll('select').forEach(sel => {
        let selected = sel.options[sel.selectedIndex];
        total += parseFloat(selected.dataset.price);
      });
      document.getElementById('totalPrice').innerText = total.toFixed(2);
      document.getElementById('finalAmount').innerText = total.toFixed(2);
    }

    function togglePortraitUpload(val) {
      const upload = document.getElementById('portraitUpload');
      if (val !== 'none') {
        upload.classList.remove('hidden');
        document.getElementById('portraitFile').setAttribute('required', 'true');
      } else {
        upload.classList.add('hidden');
        document.getElementById('portraitFile').removeAttribute('required');
      }
      calculateTotal();
    }

    function toggleTextInput(val) {
      const input = document.getElementById('textInput');
      if (val !== 'none') {
        input.classList.remove('hidden');
        input.querySelector('textarea').setAttribute('required', 'true');
      } else {
        input.classList.add('hidden');
        input.querySelector('textarea').removeAttribute('required');
      }
      calculateTotal();
    }

    function goToPage(pageNum) {
      document.querySelectorAll('.container').forEach(el => el.classList.add('hidden'));
      document.getElementById('page' + pageNum).classList.remove('hidden');
    }
  </script></body></html>
